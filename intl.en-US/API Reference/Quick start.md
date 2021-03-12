# Quick start

This topic describes how to call the SMC API by using developer tools such as Alibaba Cloud CLI, OpenAPI Explorer, and Alibaba Cloud SDK. This topic uses the CreateReplicationJob operation as an example.

Alibaba Cloud CLI is installed and configured. For more information about how to install Alibaba Cloud CLI on various operating systems, see the following topics:

-   [Windows]()
-   [Linux]()
-   [MacOS]()

## Use Alibaba Cloud CLI to call the SMC API

This example uses Alibaba Cloud CLI to call the CreateReplicationJob operation to create a migration task. Before you call the operation, read the API reference and query the required request parameters. For more information, see [API operations](/intl.en-US/API Reference/API operations.md). If an error occurs, you can view troubleshooting suggestions in the corresponding API documentation.

1.  Call the DescribeSourceServers operation to obtain the ID of the migration source:

    ```
    aliyun smc DescribeSourceServers 
    ```

2.  Run the following command to call the CreateReplicationJob operation to create a migration task:

    ```
    aliyun smc CreateReplicationJob --RegionId <TheRegionId> --SourceId s-bp1ebo013cd21t4r****
    ```

    The following command output indicates that the migration task is initiated.

    ```
    {"RequestId":"16B856F6-EFFB-4397-8A8A-CB73FA******","JobId":"j-2ze33rsym34h1hf5****"}
    ```

3.  Run the following command to call the DescribeReplicationJobs operation to query the status of the created migration task:

    ```
    aliyun smc DescribeReplicationJobs --JobId j-2ze33rsym34h1hf5****
    ```


## Use OpenAPI Explorer to call the SMC API

This example uses OpenAPI Explorer to call the CreateReplicationJob operation to create a migration task. Before you call the operation, read the API reference and query the required request parameters. For more information, see [API operations](/intl.en-US/API Reference/API operations.md). If an error occurs, you can view troubleshooting suggestions in the corresponding API documentation.

1.  Call the [DescribeSourceServers](https://api.aliyun.com/#/?product=smc&api=DescribeSourceServers&tab=DEMO&lang=JAVA) operation to obtain the ID of the migration source.

2.  Call the [CreateReplicationJob](https://api.aliyun.com/#/?product=smc&api=CreateReplicationJob&tab=DEMO&lang=JAVA) operation to create a migration task.

3.  Call the [DescribeReplicationJobs](https://api.aliyun.com/#/?product=smc&api=DescribeReplicationJobs&tab=DEMO&lang=JAVA) operation to query the status of the created migration task.


For more information about OpenAPI Explorer, see [What is OpenAPI Explorer?](/intl.en-US/Product Overview/What is OpenAPI Explorer?.md).

## Use the SMC SDK for Java to call the SMC API

This example uses the SMC SDK for Java to call the CreateReplicationJob operation to create a migration task. You can obtain the SMC SDK from [SDK](https://next.api.aliyun.com/api-tools/sdk/smc?version=2019-06-01). Before you call the operation, read the API reference and query the required request parameters. For more information, see [API operations](/intl.en-US/API Reference/API operations.md). If an error occurs, you can view troubleshooting suggestions in the corresponding API documentation.

**Note:** You must specify the <AccessKey\>, <AccessSecret\>, <RegionId\>, and <SystemDiskSize\> parameters based on your business scenario. <AccessKey\> indicates the AccessKey ID. <AccessSecret\> indicates the AccessKey secret. <RegionId\> indicates the ID of the destination Alibaba Cloud region. <SystemDiskSize\> indicates the system disk size of the destination Alibaba Cloud ECS instance. For more information, see [Create an AccessKey pair](), [Regions and zones](), and [Migration task request parameters](/intl.en-US/API Reference/Migration tasks/CreateReplicationJob.md).

```
import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.IAcsClient;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.exceptions.ServerException;
import com.aliyuncs.profile.DefaultProfile;
import com.google.gson.Gson;
import java.util.*;
import com.aliyuncs.smc.model.v20190601.*;

public class smcDemo {

    public static void main(String[] args) {
        DefaultProfile profile = DefaultProfile.getProfile("<RegionId>", "<AccessKey>", "<AccessSecret>");
        IAcsClient client = new DefaultAcsClient(profile);

        CreateReplicationJobRequest request = new CreateReplicationJobRequest();
        request.setSystemDiskSize(150);
        request.setSourceId("s-bp1ebo013cd21t4r****");

        try {
            CreateReplicationJobResponse response = client.getAcsResponse(request);
            System.out.println(new Gson().toJson(response));
        } catch (ServerException e) {
            e.printStackTrace();
        } catch (ClientException e) {
            System.out.println("ErrCode:" + e.getErrCode());
            System.out.println("ErrMsg:" + e.getErrMsg());
            System.out.println("RequestId:" + e.getRequestId());
        }
    }
}
```

