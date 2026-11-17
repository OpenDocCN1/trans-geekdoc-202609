These checks are run using pytest.

```
```python
1. #Import libraries
2. import pytest
3. #Import files/modules
4. from prediction_model.config import config
5. from prediction_model.processing.data_management import load_dataset
6. from prediction_model.predict import make_prediction
7.
8. @pytest.fixture
9. def single_prediction():
10. ''' This function will predict the result for a single record'''
11. test_data = load_dataset(file_name=config.TEST_FILE)
12. single_test = test_data[0:1]
13. result = make_prediction(single_test)
14. return result
15.
16.#Test Prediction
17. def test_single_prediction_not_none(single_prediction):
18. ''' This function will check if the result of prediction is not None'''
19. assert single_prediction is not None
20. def test_single_prediction_dtype(single_prediction):
21. ''' This function will check if the data type of the result of the prediction is str i.e. string'''
22. assert isinstance(single_prediction.get('prediction')[0], str)
23. def test_single_prediction_output(single_prediction):
24. ''' This function will check if the result of the prediction is Y'''
25. assert single_prediction.get('prediction')[0] == 'Y'
```
```