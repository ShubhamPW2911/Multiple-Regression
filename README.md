import numpy as np
import matplotlib.pyplot as plt
from sklearn import datasets, linear_model
from sklearn.metrics import mean_squared_error

# dict_keys(['data', 'target', 'frame', 'DESCR', 'feature_names', 'data_filename', 'target_filename', 'data_module'])
diabetes = datasets.load_diabetes()
print(diabetes.DESCR)

diabetes_x=diabetes.data
diabetes_train_x=diabetes_x[-30:]
diabetes_test_x=diabetes_x[:30]
print(diabetes_test_x)

diabetes_train_y=diabetes.target[-30:]
diabetes_test_y=diabetes.target[:30]

model=linear_model.LinearRegression()
model.fit(diabetes_train_x, diabetes_train_y)

diabetes_predict_y=model.predict(diabetes_test_x)
custom_model=model.predict(np.array([[4.80759064e-02, 6.06801187e-02, 6.16962065e-02, 2.18723550e-02, -4.42234984e-02, -3.48207628e-02, -4.34008457e-02, -2.59226200e-03, 1.99084209e-02, -1.76461252e-02]]))
print('Custom prediction: ', custom_model)

print('Mean squared error: ',mean_squared_error(diabetes_test_y, diabetes_predict_y))
print('Weights: ',model.coef_)
print('Intercept: ', model.intercept_)
