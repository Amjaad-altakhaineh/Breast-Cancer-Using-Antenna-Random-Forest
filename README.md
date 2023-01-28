# Breast-Cancer-Using-Antenna-Random-Forest
The project findings indicate that the prediction of the size and location of the malignant tumor using the antenna technique dataset based on electromagnetic waves performs better in comparison to the other traditional techniques. The machine learning RF-based are tested in Python
---- Abstract---: This project proposes a new method that extracts features based on the electromagnetic wave parameters obtained from the compact antenna for breast cancer size and its location detection using machine learing. The electromagnetic signals are transmitted via an antenna from one end of the breast (inside the breast) and are received on the other end (outside the breast). Therefore, these signals can pass through the cancer tumor (which looks like an obstacle), and these signals/waves can defect and vary with different tumor cases (sizes and locations). By doing so, the tumor's size and location can be predicted easily. To this end, the regression performance of these datasets for breast cancer size and location is tested using multi-output regression random forest. The project findings indicate that the prediction of the size and location of the malignant tumor using the antenna technique dataset based on electromagnetic waves performs better in comparison to the other traditional techniques. The deep learning are tested in Python on different sets of data to determine their accuracy and performance

1- Aim and objectives: This project aims and contributes to monitoring and predicting the size and location of the tumor in its early stages without the need to go to the doctor using radio waves emitted from the antennas, where an antenna was built inside the breast (the transmitter) and the other outside the breast (the receiver). Starting at 1 mm, place the antenna in three directions

2- Proposed dataset: Due to time constraints, as data extraction takes a full month, two datasets were extracted, the first with three features with 973 rows , and the second with six features with 199 rows . To this end, in this folder you will see to py.codes for the both dataset using the same Random Forest models The first which refere to the first dataset ( Breast-Cancer-1) and the secound one for the secound dataset ( Breast-Cancer-2)

3- Methodology: The proposed datasets will be extracted from electromagnetic waves received by a receiving antenna (located outside the breast), as the data includes electrical measured quantities like (Transmitted power, Gain, Radiation Efficiency, voltage, current, and impedance). In order to anticipate the condition of the tumor, the machine-learning model will be updated whenever the antenna measures a new value. - Transmitted power: The amplitude, intensity, or total power of a transmitted wave in relation to an incident wave is described by a transmission coefficient. -Gain: The gain of a receiving antenna indicates how effectively the antenna transforms radio waves coming from a specific direction into electrical power. -Radiation Efficiency: In a receiving antenna, it refers to the percentage of the radio wave's power that is actually supplied as an electrical signal after being intercepted by the antenna. - Voltage: The difference in electric potential between two places is often referred to as electric pressure, electric tension, or (electric) potential difference. and is easily measurable. - Current: An electric current is a flow of positively or negatively charged particles, such as electrons or ions, that travels through an electrical conductor or a vacuum. The net rate of flow of electric charge through a surface or into a control volume is used to calculate it. - Impedance An object's electrical resistance is a measurement of how easily an electric current travels through it. The methodology consists of multi phases as explained below.

4- Proposed Design, Data acquisition, and processing The simulated/measured electric data from the simulated microstrip antennas is collected using the CST simulator . The 3D breast model was created using a variety of materials [16]. It is crucial to ensure that the breast has permittivity-based dielectric properties that are comparable to those of real breasts. The permittivity (ε_skin=17.7,ε_fat=3.4,ε_Fiber=16,ε_Tumor=18 ) indicates the electrical characteristics of the substance that would allow electromagnetic waves to determine if the substance or cell is malignant or not, such as a gland, by the presence or absence of certain electrical qualities. The breast employed in this study followed the same design recommendations made by earlier researchers . The original region/place where the tumor is designed is inside the breast, in the middle of the breast. For testing, several tumor sizes (radices) ranging from 1 to 2.2 mm are produced


![image](https://user-images.githubusercontent.com/123154408/215289012-4640ad72-28b2-4080-88c8-b6ba98648f0e.png) ![image](https://user-images.githubusercontent.com/123154408/215289019-f1bee9f5-7fb4-4faf-8c8c-af7571078007.png) ![image](https://user-images.githubusercontent.com/123154408/215289064-ee685034-0858-460b-bc69-bcfe9ef6171b.png)

Creating a Multi-output Regersor with scikit-learn (Random forest Multi-output Regersor)
A powerful and user-friendly Python package for machine learning is Scikit-learn. When creating and setting up your machine learning models, many choices must be made. The majority of these choices must be made empirically, by learning from mistakes and basing conclusions on actual data. As a result, it is vitally necessary to have a reliable method of assessing how well your random forest models are working. We will learn how to assess model performance using scikit-learn in this subsection. With scikit-learn, building a multi-label Regersor is simple In actuality, there are only a few minor differences from building a standard Regersor. Let's look at the procedures needed to construct the dataset and the related Python code. In order to read the dataset and handle it:
a-	 Imports: Importing all of the necessary Python dependencies is the first step. To read and process the data, we'll utilize three packages: Pandas, Numpy, and Matplotlib. Sklearn is generally used for tasks related to data preprocessing and for the multi-output regresor. We may import data from Sklearn and create train test split, which allows us to divide the data into a training dataset and a testing dataset. Additionally, we will design our Random forest Multi-output Regersor model utilizing metrics, Randomforest, and multioutput from Sklearn. Additionally, we will use the parameter n estimate for process improvement and optimization.

b-	Importing and Explore the Datasets: the next step is Importing and reading the datasets, both datasets used were saved using two CSV files, where the first one is saved in the name “Breast_Cancer_1” and read and shows the first five rows using the code data. head(), as is the case with the second called “ Breast_Cancer _2”. In addition, use the data.info() to give full detail about the type of datasets used and to give a broad overview of its size in terms of the number of features and samples, as the same is used to read the two CSV files.  we print a quick overview of the datasets using the data.info() function. 

c-	Identify Anomalies/ Missing Data: Since this dataset is real-time measured data, there are not any data points that immediately appear as anomalous and no missing data in any of the measurement columns. To verify our claim, the actual codes of null and duplicate are written and adopted. It can be seen in the Jupiter file results that there are no missing data or duplicates. Furthermore, by closely looking at the results, all of the data points are floats, so there is no categorical data and, therefore, no need to use one of the encoder methods. For demonstration, two files explain each data set and those observations are common for both datasets.

d-	Features and Targets and Convert Data to Arrays: Now, it needs to separate the data into the features and targets. The target, also known as the label, is the value we want to predict, in this case, the actual tumor size (Tumor_rad) and its location in three coordinates (Tx, Ty, and Tz) and the features are all the columns the model uses to make a prediction. In our case, there are two stages of features the first one referred to the  (S21, Efficiency, and gain ) features while these features are increased to Six ( S21, Efficiency, gain, Voltage, Current, Impedance). We will also convert the Pandas data frames to Numpy arrays because that is the way the algorithm works. For the first dataset of ( Breast_Cancer_1), select all rows and the first 3 columns (from 0 to 3)  from the dataset to X and all rows and the last 4 columns (from 3 to 7)    as y. While the same mechanism is adopted for the second dataset ( Breast_Cancer_2), since the features are increased the X will include an extra three features, therefore, select all rows and the first 6 columns (from 0 to 6) from dataset to X and all rows and the last 4 columns (from 6 to 10)    as y. As shown below. 
e-	Train/test split :You can explicitly define the dataset to use for validation and testing during training with Sklearn. We must divide the dataset into training and testing data after it has been generated. Train test split, another useful function from Scikit-learn, is available for this. Since both datasets are tiny, we divide X and Y into their training and testing components in this project using a 90/10 train/test split. In other words, 90% of the samples from the first and second datasets will be used for training and 10% for testing. On the testing end, this split is not very significant; 80/20 splits are also frequent. It is important to keep in mind that the random state in this case is one of the optimization factors that can be altered arbitrarily based on getting the model to perform well. The public domain states that Random State is either 42 or 0.

f-	Creating the Random forest multi-output regressor model: The next step is creating the regr_multirf model using a MultiOutputRegressor and RandomForestRegressor of the sklearn.multioutput and sklearn.ensemble respectively. Using n_estimators=500, allows us to detect many patterns at first. As is common, we use n_estimators as an optimizer in order to enhance the performance of the model. As we know, a n_estimators  parameter generates trees that are used in the prediction. In general, you should always tune your model as it must help to enhance the algorithm’s performance. As you might know, tuning is a really expensive process time-wise. When tuning a Random Forest model it gets even worse as you must train hundreds of trees multiple times for each parameter grid subset. So, you must not be afraid. Trust me, it is worth it. We set the number of trees there to 500. So that this value is chosen randomly according to the principle of trial and error, where it was observed at this value that the performance of the model is better and has a higher accuracy value.

g-	Training the model: The model must now be trained using data, and some of the already established configuration choices must be made available. All you have to do is use the predict method on the test set and the fit method on your training set. Now the model will begin training.

h-	Evaluating the model: The model can be assessed using regr multirf.predict after being trained on both datasets. We then know how well it performs when employed on data that it has never seen before based on the testing dataset.

i-	Model Performance Measurement As previously indicated, Testing It's time to test your model's ultimate performance once you've trained and tuned it. Since Random Forest is just another regression technique, you may evaluate its performance using any regression statistic. You could make use of MAE, MSE, MASE, RMSE, MAPE, SMAPE, and other models. However, based on my observations, MSE and MAE are the most frequently employed. To assess the effectiveness of the model, both of them will be a good fit. The error of the perfect model will be equal to zero, thus if you utilize them, keep in mind that the less your error, the better. R2 can be used to present the performance of the model as a percentage of 100% for accuracy metrics





