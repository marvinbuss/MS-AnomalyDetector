# Anomaly Finder (REST API) - Jupyter notebook
This Jupyter notebook can be used to detect anomalies with the Microsoft Cognitive Service - Anomaly Detector. This is a RESTful web service that can be used easily embed anomaly detection capabilities into your apps so your users can quickly identify problems to minimize loss and customer impact.

The service requires no extensive knowledge about machine learning techniques. The user can simply use the API to ingest time-series data of all types and volumes and make use of the pre-trained AI models that are included in the service. The service selects the best-fitting anomaly detection model for your data to ensure high accuracy, and automatically surfaces incidents as soon as they happen.

Use Anomaly Detector to identify business incidents, monitor IoT device traffic, manage fraud, respond to changing markets, and more.

## Parameters
The parameters can be understood as settings and are adjustable according to your requirements. The variables have the following purpose within the notebook:

* `BATCH_DETECTION_URL`: Endpoint path for the prediction of anomalies for a whole batch of timeseries data. Generally, this value must not be changed by the user.
* `LATEST_POINT_DETECTION_URL`: Endpoint for the prediction of anomalies for the last point in the timeseries data. Generally, this value must not be changed by the user.
* `ENDPOINT`: Endpoint of the Cognitive Service. The Anomaly Finder service can be deployed in different Azure regions and the region in the endpoint URI must be adjusted accordingly. The base URL has the following format, whereas the correct region must be inserted in `<your-region>` (e.g. `westeurope`, `westus2`, etc.): `https://<your-region>.api.cognitive.microsoft.com/`
* `SUBSCRIPTION_KEY`: Insert the subscription key of your Anomaly Finder deployment. This can be found in the Azure Portal. 
* `USE_POWER_BI`: `True`, if you want to stream data to Microosft Power BI and `False`, if you don't. Please read the next section for more details.
* `POWER_BI_REST_API_URL`: Streaming data endpoint for Power BI. Please read the next section for more details.
* `TIMESTAMP_COL_NAME`: Header name of the timestamp column.
* `VALUE_COL_NAME`: Header name of the value column.
* `DATETIME_FORMAT`: Change the value according to your datetime format in the csv file.

## Power BI integration
For the latest point anomaly detection I implemented a data streaming functionality to Power BI. This allows to create real-time dashboards that present the current status of the timseries and allow to quickly view and react according to the results. To use this, please follow steps below:

1. Login to [Power BI](https://powerbi.microsoft.com/en-us/).
2. Open `My Workspace`.
3. Click on `+ Create`.
4. Create a new streaming dataset.
5. Select a name for the dataset.
6. Add values to the dataset (see image below).
7. Copy the `Push URL` of the streaming dataset and assign the value to the `POWER_BI_REST_API_URL` variable.
8. Set `USE_POWER_BI` to `True`.
9. Run one of the cells in 6.2.

<img src="media/powerbi.png" alt="Power BI Streaming dataset" width="300"/>

## Anomaly Finder documentation
Find more details about the use of the Anomaly Finder on the following website: https://docs.microsoft.com/en-us/azure/cognitive-services/anomaly-detector/

For more information on how to deploy the Cognitive Service on Azure, please read: https://docs.microsoft.com/en-us/azure/cognitive-services/cognitive-services-apis-create-account