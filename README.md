Download Link: https://assignmentchef.com/product/solved-comp5318-assignment-1-classification
<br>
<h1> Dataset preparation</h1>

<h2>The data</h2>

The dataset for this assignment is the Breast Cancer Wisconsin. It contains 699 examples described by 9 numeric attributes. There are two classes – <strong>class1 </strong>and <strong>class2</strong>. The features are computed from a digitized image of a fine needle aspirate of a breast mass of the subject. Benign breast cancer tumours correspond to <strong>class1 </strong>and malignant breast cancer tumours correspond to <strong>class2.</strong>

The dataset should be downloaded from Canvas: <strong>breast-cancer-wisconsin.csv</strong>. This file includes the attribute (feature) headings and each row corresponds to one individual. Missing attributes in the dataset are recorded with a <strong>‘?’</strong>.

<h2>Data pre-processing</h2>

You will need to pre-process the dataset, before you can apply the classification algorithms. Three types of pre-processing are required:

<ol start="5">

 <li>The <strong>missing attribute values</strong> should be replaces with the mean value of the column using impute.<strong>SimpleImputer</strong>.</li>

 <li><strong>Normalisation</strong> of each attribute should be performed using a min-max scaler to normalise the values between [0,1] with preprocessing.<strong>MinMaxScaler</strong>.</li>

 <li>The classes <strong>class1</strong> and <strong>class2</strong> should be changed to <strong>0</strong> and <strong>1</strong></li>

 <li>The value of each attribute should be formatted to 4 decimal places using .4f.</li>

</ol>

The correctness of your pre-processed data will be automatically tested by PASTA. Thus, you need to make sure that you follow the input and output instructions carefully.

<h2>2.      Classification algorithms with 10-fold cross-validation</h2>

You will now apply multiple classifiers to the pre-processed dataset, in particular: Nearest Neighbor, Logistic Regression, Naïve Bayes, Decision Tree, Bagging, Ada Boost and Gradient Boosting. All classifiers should use the <strong>sklearn</strong> modules from the tutorials<strong>.</strong> All random states in the classifiers should be set to <strong>random_state=0</strong>.

You need to evaluate the performance of these classifiers using 10-fold cross validation from <strong>sklearn.model_selection.StratifiedKFold</strong> with these options: <strong>cvKFold=StratifiedKFold(n_splits=10, shuffle=True, random_state=0) </strong>

For each classifier, write a function that accepts the required input and that outputs the average crossvalidation score: <strong>def exampleClassifier(X, y, [options]): </strong>

<strong>                … </strong>

<strong>return scores, scores.mean() </strong>

where <strong>X</strong> contains the attribute values and <strong>y</strong> contains the class (as in the tutorial exercises).

More specifically, the headers of the functions for the classifiers are given below:

<h3>K-Nearest Neighbour</h3>

<strong>def kNNClassifier(X, y, K) </strong>

It should use the KNeighboursClassifier from sklearn.neighbours.

<h3>Logistic Regression</h3>

<strong>def logregClassifier(X, y) </strong>

It should use LogisticRegression from sklearn.linear_model.

<h3>Naïve Bayes</h3>

<strong>def nbClassifier(X, y) </strong>

It should use GaussianNB from sklearn.naive_bayes

<h3>Decision Tree</h3>

<strong>def dtClassifier(X, y) </strong>

It should use DecisionTreeClassifier from sklearn.tree, with information gain (the entropy criterion)

<h3>Ensembles</h3>

<strong>def bagDTClassifier(X, y,</strong> <strong>n_estimators, max_samples, max_depth) def adaDTClassifier(X, y, n_estimators, learning_rate, max_depth) def gbClassifier(X, y, n_estimators, learning_rate) </strong>

These    functions             should   implement          Bagging,               Ada        Boost     and        Gradient              Boosting using BaggingClassifier, AdaBoostClassifier    and GradientBoostingClassifier from sklearn.ensemble. All should combine Decision Trees with information gain.

<h2>3.       Parameter Tuning</h2>

For two other classifiers, Linear SVM and Random Forest, we would like to find the best parameters using grid search with 10-fold stratified cross validation (GridSearchCV in sklearn).

The split into training and test subsets should be done using train_test_split from sklearn.model_selection with stratification and random_state=0 (as in the tutorials but with random_state=0).

Hint: You need to pass StratifiedKFold as an argument to GridSearchCV, not cv=10 as in the tutorials. This ensures that random_state=0.

Write the following functions:

<h3>Linear SVM</h3>

<strong>def bestLinClassifier(X,y) </strong>

It should use SVC from sklearn.svm.

The grid search should consider the following values for the parameters C and gamma: C = {0.001, 0.01, 0.1, 1, 10, 100}  gamma = {0.001, 0.01, 0.1, 1, 10, 100}

The function should print the best parameters found, the best-cross validation accuracy score and the best test set accuracy score, see Section 4.

<h3>Random Forest</h3>

<strong>def bestRFClassifier(X,y) </strong>

It should use RandomForestClassifier from sklearn.ensemble with information gain and max_features set to ‘sqrt’.

The grid search should consider the following values for the parameters n_estimators and max_leaf_nodes:

n_estimators = {10, 30} max_leaf_nodes = {4, 16}

The function should print the best parameters found, best-cross validation accuracy score and best test set accuracy score, see Section 4.

<h2>4.       Submission details – PASTA</h2>

This assignment is to be submitted electronically via the PASTA submission system.

<h3>How to submit to PASTA</h3>

Your program will need to be named MyClassifier. If you use Jupyter notebook to write your code, please do the following:

<ol>

 <li>Ensure that you have a main method that is able to parse 3 command line arguments. PASTA will run your code with 3 different arguments. Details about the 3 arguments are given below.</li>

 <li>Ensure that you export your Jupyter notebook as Python code and only submit the Python code to PASTA.</li>

</ol>

Before submitting to PASTA please make sure that all your Python programs (MyClassifier.py and all other supporting .py programs, if you have any) are zipped together. If you only have 1 Python program (MyClassifier.py), you do not need to zip it. Just submit that file to PASTA.

If you are zipping, please do <strong><u>not</u></strong> zip the folder containing your MyClassifier.py program (and your other supporting programs, if any). Zip only the .py files. To do this, select the MyClassifier.py file (and your other supporting scripts if any), right click, and compress/zip them. Then submit the resulting zip file to PASTA.

Detailed submission instructions:

<ul>

 <li>Find Assignment 1 and press “Submit” (the red icon on the right). Then press “Choose File” and attach the file, then press “I accept” after reading the University policy on academic honesty and agreeing with it.</li>

 <li>If you see a message indicating that your code is queued for testing, this means that your code has been uploaded successfully.</li>

 <li>If you see a red error box, you need to fix any problems indicated before your submission will be accepted.</li>

 <li>Once your program has been tested, the page will tell you to refresh for results, so refresh the page. You should see green and red boxes. Each box corresponds to a test; a red box indicates that your program has failed the respective test and a green box indicates that your program has passed the test.</li>

 <li>If you have red boxes, you can see which tests were not passed by clicking on Assignment 1. Correct the errors (go back to Jupyter, re-write your code and test it carefully) and then submit again in PASTA.</li>

</ul>




Important:

<ul>

 <li>Do not treat PASTA as your development environment! You must firstly test your code on your laptop or desktop computer to make sure it runs without errors and only after that submit to PASTA. If you don’t do this, there will be too many submissions in the queue and the waiting time to run your code will become very long. In this case, we may need to limit the number of submissions per student; currently it is unlimited.</li>

 <li>Start working on the assignment as soon as possible and do not delay the submission till the last moment as PASTA will get very busy and you risk being late.</li>

</ul>

<strong> </strong>

<h3>Input</h3>

Your program should take 3 command line arguments:

<ol>

 <li>The first argument is the path to the data file.</li>

 <li>The second argument is the name of the algorithm to be executed or the option for print the preprocessed dataset:

  <ol>

   <li><strong>NN</strong> for Nearest Neighbour.</li>

   <li><strong>LR </strong>for Logistic Regression.</li>

   <li><strong>NB </strong>for Naïve Bayes.</li>

   <li><strong>DT </strong>for Decision Tree.</li>

   <li><strong>BAG </strong>for Ensemble Bagging DT.</li>

   <li><strong>ADA </strong>for Ensemble ADA boosting DT.</li>

   <li><strong>GB </strong>for Ensemble Gradient Boosting.</li>

   <li><strong>RF </strong>for Random Forest.</li>

   <li><strong>SVM </strong>for Linear SVM.</li>

   <li><strong>P </strong>for printing the pre-processed dataset</li>

  </ol></li>

 <li>The third argument is <strong>optional</strong>, and should <strong>only be</strong> <strong>supplied</strong> to algorithms which require parameters, namely NN, BAG, ADA and GB. It is the path to the file containing the parameter values for the algorithm. The file should be formatted as a csv file like in the following examples:

  <ol>

   <li>NN (note the capital K); an example for 5-Nearest Neighbour:</li>

  </ol></li>

</ol>

K

5

<ol>

 <li>BAG:</li>

</ol>

n_estimators,max_samples,max_depth

100,100,2

<ol>

 <li>ADA:</li>

</ol>

n_estimators,learning_rate,max_depth

100,0.2,3

<ol>

 <li>GB:</li>

</ol>

n_estimators,learning_rate

100,0.2

For algorithms which do not require any parameters (LR, NB, DT, RF, SVM, P), the third argument should not be supplied.

The file paths (the first and third arguments) represent files that will be supplied to your program for reading. You can test your submission using any files you like, but PASTA will provide your submission with its own files for testing, so do not assume any specific filenames.

<strong>Your program must be able to correctly infer X and y from the file. </strong>Please do not hard-code the number of features and examples. For the last few tests we will use a dataset with different number of features and examples than the given breast cancer dataset. The new dataset will contain a header line and the last column will correspond to the class, as the given breast cancer dataset.

The following examples show how your program would be run:

<ol>

 <li>We want to run the k-Nearest Neighbour classifier, the data is in a file called <strong>breast-cancerwisconsin-normalised</strong>.<strong>csv</strong>, and the parameters are stored in a file called <strong>csv</strong>:</li>

</ol>

python MyClassifier.py breast-cancer-wisconsin-normalised.csv NN param.csv

<ol start="2">

 <li>We want to run Naïve Bayes and the data is in a file called breast-cancer-wisconsinnormalised.csv.</li>

</ol>

python MyClassifier.py breast-cancer-wisconsin-normalised.csv NB

<ol start="3">

 <li>We want to run the data pre-processing task and the data is in a file called <strong>breast-cancerwisconsin</strong>.<strong>csv:</strong></li>

</ol>

python MyClassifier.py breast-cancer-wisconsin.csv P

Only option P assumes <u>non-pre-processed</u> input data (and it needs to pre-process and print this data). All other options (NN, LR, etc) assume already <u>pre-processed</u> data (i.e. normalized, scaled, missing values replaced, etc) and don’t need to do any data pre-processing.

<h3>Output</h3>

Your program will output to standard output (i.e. “the console”).

<h4>Pre-processing task</h4>

For option P, you will need to output your pre-processed data onto the console using the print command.

Let’s assume your normalised data looks like the following:

<table width="642">

 <tbody>

  <tr>

   <td width="75">ClumpThickness</td>

   <td width="66">Uniformi ty of Cell Size</td>

   <td width="66">Uniformity of CellShape</td>

   <td width="66">Marginal Adhesion</td>

   <td width="69">SingleEpithelialCell Size</td>

   <td width="64">Bare Nuclei</td>

   <td width="66">Bland Chromati n</td>

   <td width="66">Normal Nucleoli</td>

   <td width="57">Mitoses</td>

   <td width="47">Class</td>

  </tr>

  <tr>

   <td width="75">0.1343</td>

   <td width="66">0.4333</td>

   <td width="66">0.5432</td>

   <td width="66">0.8589</td>

   <td width="69">0.3737</td>

   <td width="64">0.9485</td>

   <td width="66">0.4834</td>

   <td width="66">0.9456</td>

   <td width="57">0.4329</td>

   <td width="47">0</td>

  </tr>

  <tr>

   <td width="75">0.1345</td>

   <td width="66">0.4432</td>

   <td width="66">0.4567</td>

   <td width="66">0.4323</td>

   <td width="69">0.1111</td>

   <td width="64">0.3456</td>

   <td width="66">0.3213</td>

   <td width="66">0.8985</td>

   <td width="57">0.3456</td>

   <td width="47">1</td>

  </tr>

  <tr>

   <td width="75">0.4948</td>

   <td width="66">0.4798</td>

   <td width="66">0.2543</td>

   <td width="66">0.1876</td>

   <td width="69">0.9846</td>

   <td width="64">0.3345</td>

   <td width="66">0.4567</td>

   <td width="66">0.4983</td>

   <td width="57">0.2845</td>

   <td width="47">0</td>

  </tr>

 </tbody>

</table>




Then your program output should look like this:

0.1343,0.4333,0.5432,0.8589,0.3737,0.9485,0.4834,0.9456,0.4329,0 0.1345,0.4432,0.4567,0.4323,0.1111,0.3456,0.3213,0.8985,0.3456,1

0.4948,0.4798,0.2543,0.1876,0.9846,0.3345,0.4567,0.4983,0.2845,0

You must print the feature values to 4 decimal places as in the example above, e.g. 0.1 should be printed as 0.100. The class value is an integer.

Note also that there is no new line character after the last line. To print the last line, ensure you pass empty character as the end parameter for the print statement.

print(data, end=’’)

<h4>Classifiers with 10-fold cross validation task</h4>

Your classifier should only print the mean accuracy score with precision of 4 decimal places using .4f. Note that .4f does rounding too. For example, if your mean accuracy is 0.987689, your program output should look as follows:

0.9877

Note: There is no new line character after the accuracy. See above how to print like this.

<h3>Parameter tuning task</h3>

For Linear SVM, your program should output <strong>exactly 4 lines</strong>. The first line contains the optimal C value, the second line contains the optimal gamma value, and the third line contains the best cross-validation accuracy score formatted to 4 decimal places using .4f and the fourth line contains the test set accuracy score also formatted to 4 decimal places. For instance, if the optimal C and gamma values are 0.001 and 0.1 respectively, and the two accuracies are 0.999874 and 0.952512, your program output should look like this:

0.001

0.1

0.9999

0.9525

For Random Forest, your program should output <strong>exactly 4 lines. </strong>The first line contains the optimal n_estimators, the second line contains the optimal max_leaf_nodes, the third line contains the best cross validation accuracy score truncated to 4 decimal places using .4f and the fourth line contains the test set accuracy score also truncated to 4 decimal places. For instance, if the optimal n_estimators and max_leaf_nodes are 10 and 4 respectively, and the two accuracies are 0.997623 and 0.87243, your program output should look like this:

10

4

0.9976

0.8724


