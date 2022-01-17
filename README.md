# Cantilever_Family_Recursive_GNN

### Flow
![flow](https://user-images.githubusercontent.com/56711947/149752304-91036140-2b30-4a33-9503-1f31483317d0.jpg)  

### Data preprocessing
1. Save all the sequence of topology optimization  
2. Decide the number of intermediate material density (6 in this repository)  
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

### Results
Recursive process is needed to get optimal topology prediction with trained model  
Gaussian noise added at input material density to alleviate error accumulation  
![recursive](https://user-images.githubusercontent.com/56711947/149759038-c2e0afbb-6b36-4391-97a3-d2192d9a5a0a.jpg)  
![results](https://user-images.githubusercontent.com/56711947/149759545-6efb2805-4fe7-4604-95ec-5b4d52959f1e.jpg)
Compliance scatter plot and coefficient of determination  
![compliance scatter plot](https://user-images.githubusercontent.com/56711947/149759969-7eafa693-1480-45db-9eb6-821b0e6fbf61.jpg)
