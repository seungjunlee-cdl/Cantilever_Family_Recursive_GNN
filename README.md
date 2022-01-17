# Cantilever_Family_Recursive_GNN

### Flow
![flow](https://user-images.githubusercontent.com/56711947/149752304-91036140-2b30-4a33-9503-1f31483317d0.jpg)  

### Data preprocessing
1. Save all the sequence of topology optimization  
2. Decide the number of intermediate material density
3. Save sequence including first and last iteration  
4. Build single dataset with decided length  
![recursive data](https://user-images.githubusercontent.com/56711947/149762004-34822344-9254-43ff-8f2f-b99da630786a.jpg)

### Input & output node features
Input node features  
1. 1st iteration displacement of topology optimization  
2. 1st iteration stress of topology optimization  
3. Specific intermediate material density  

Output node features
1. Next sequence of input material density
![input and output](https://user-images.githubusercontent.com/56711947/149757542-1ec724e9-6b1e-4ba4-8a19-af8fc4816957.jpg)

### Model architecture
19 graph attention layer with batch normalization, dropout and L2 regularization  
Used residual connection in hidden node features  
![model](https://user-images.githubusercontent.com/56711947/149758267-ea8a01a1-defa-418c-8e96-bcc87105479c.jpg)  
Learning rate -> Cosine annealing warm restarts  
![lr](https://user-images.githubusercontent.com/56711947/149761125-712885bf-39c0-4b16-8dee-90a863c0425e.jpg)

### Training Strategy
Previous predicted material density to next step training's input  
![training strategy](https://user-images.githubusercontent.com/56711947/149762648-b9949cc6-eebc-4261-8e6c-84bc96431c0b.jpg)


### Results
Training and validation loss with different number of intermediate naterial density  
![seq num](https://user-images.githubusercontent.com/56711947/149763039-5e72d91c-4b19-4a20-b814-34b3f9ec8b30.jpg)

|Model|Validation loss|
|------|---|
|3 sequence model|0.1138|
|6 sequence model|0.1110|
|9 sequence model|0.1208|
|12 sequence model|0.1274|
|15 sequence model|0.1315|

![res](https://user-images.githubusercontent.com/56711947/149764415-528d21c7-5a92-48d0-b379-fb836768c1c3.jpg)
Compliance scatter plot and coefficient of determination  
![scatter](https://user-images.githubusercontent.com/56711947/149763841-62efb11a-d772-4dc9-b73c-d89a76e1632a.jpg)
