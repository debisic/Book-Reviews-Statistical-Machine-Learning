This book review analysis is an end to end machine learning pipeline project handled as a team of 3 persons, the owner of this repository and the other two in the credits session. The dataset used is a curation from the [googreads](https://www.goodreads.com/) website. There is a python notebook used for data exploration and it can be found in the `project_report` folder. The following models were used in this work:

- DecisionTreeClassifier
- XGBClassifier
- RandomForestClassifier
and the RandomForestClassifier had better performance in training `accuracy`, `precision`, `recall` and `f1_score` according to the results in the bellow table.



|   Model              |   accuracy_train   |   precision_weighted_train   |   recall_weighted_train   |   f1_weighted_train   |
|----------------------|--------------------|------------------------------|---------------------------|-----------------------|
|DecisionTreeClassifier|     0.8494         |            0.8478            |         0.8494            |          0.8481       |
|XGBClassifier         |     0.8814         |            0.8807            |         0.8814            |          0.8806       |
|RandomForestClassifier|     0.8931         |            0.8931            |         0.8931            |          0.8926       |



# How to run the project!

Make a new folder in your local and clone the repository with this link.

```
https://github.com/debisic/google_reads_ML_pipeline.git
```
Get in the books_project directory

```
cd google_reads_ML_pipeline

```

**STARTING DOCKER**

### Method 1 (Iterative)

1. Open the Dockerfile and comment the CMD["python3","train.py"] then map with volume on your local pc

2. Build the docker images, here the image is named `books`
```

docker build . -t books -f src/Dockerfile

```
3. Run the image in a container

```
docker run -it -v "/host/path":/app books

```

*/host/path : path is the local directory that contains the project root folder usually like this for a windows machine (c/users/.../google_reads_ML_pipeline)<br>

4. Once you have started the container, run the train.py script like this and observe the outputs till the end, then exit the container.


```
python3 train.py > ./../project_report/results.txt

```
From that command, All outputs of the train.py will be directed to results.txt inside project_report folder.

With method 1 you have access to the container and the docker is mapped to the books_project directory on your local pc.<br>
**You can then easily check the results of training by opening the runs directory on your pc**.

### Method 2 (Declarative)
1. Open the Dockerfile and Uncomment the CMD["python3","train.py"] in line 19

2. Build the docker images

```
docker build . -t books -f src/Dockerfile

```
3. Run the image in a container by running the command below (model automatically start training 3 models decision tree, xgboost and random forest.)

```
docker run -it books 

```
# NB
The workflow can be managed by running it in the github actions as well, the workflow file is well configured to allow the exploration of this work should the reader not take interest in having the files on their local machine. The results can be downloaded from the artifacts session of the Github.
## Special Credit:
- John-Luc Boatiemele
- Deogratis Allakonoon