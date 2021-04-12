####Customer Environment Pipeline Flow
![piepline flow](./images/pipeline/pipeline/pipelineFlow.png)

1. Linked service for source blob storage is created by using **SAS URI** of source blob storage.
![piepline flow](./images/pipeline/pipeline/publicLinkedService.png)
customerLinkedService.png

2. Linked service for customer blob storage is created where data will be copied
![piepline flow](./images/pipeline/pipeline/customerLinkedService.png)

3. Copy activity is used to get data from source to customer environment. In the source of copy data dataset **PublicEnDataset** is selected which contains reference of source blob storage.
   In the parameter container name is given which contains the data. In the wildcard path of all folders is given as shown below.
![piepline flow](./images/pipeline/pipeline/pipelineSource.png)

4. In the sink of copy actiity destination (customer) container name is given where data will be copied.
![piepline flow](./images/pipeline/pipeline/pipelineSink.png)

5. Inside the source of copy activity **Filter by last modified** property **Start Time (UTC)** is **@adddays(utcnow(),-1)** which will get the files which are updated or created in the last 24 hours

![piepline flow](./images/pipeline/pipeline/filerLastModified.png)


