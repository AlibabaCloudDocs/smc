# Quick start {#concept_610098 .concept}

This topic uses CreateReplicationJob to demonstrate how to call the SMC API through developer tools such as Alibaba Cloud CLI, OpenAPI Explorer, and Alibaba Cloud SDK.

## Use OpenAPI Explorer to call the SMC API {#section_qur_cx3_phy .section}

This example uses Alibaba Cloud CLI to call the operation to create a migration task. Before calling the operation, read the instructions in the API documentation and query the values of required request parameters. If an error occurs during API calling, you can view troubleshooting suggestions in the corresponding API documentation.

 **Prerequisites** 

Make sure that you have installed and configured Alibaba Cloud CLI. For detailed steps, see [Install CLI](../../../../reseller.en-US/Installation Guide/Overview.md#) and [Configure CLI](../../../../reseller.en-US/Configure Alibaba Cloud CLI/Configure credential/Overview.md#).

 **Procedure** 

To call the operation from Alibaba Cloud CLI, perform the following steps:

1.  Run the following command to obtain the IDs of migration sources:

    ``` {#codeblock_bjy_wkd_cbx .lanuage-shell}
    aliyun smc DescribeSourceServers 
    ```

2.  Run the following command to call the CreateReplicationJob operation to create a migration task:

    ``` {#codeblock_ecy_9wk_bkl .lanuage-shell}
    aliyun smc CreateReplicationJob --RegionId <TheRegionId> --SourceId s-bp1ebo013********1jv
    ```

    If the following information is returned, migration task creation has been initiated.

    ``` {#msgblock_fic_16u_90s}
    {"RequestId":"16B856F6-EFFB-4397-8A8A-CB73FA******","JobId":"j-2ze33rsym********srq"}
    ```

3.  Run the following command to call the DescribeReplicationJobs operation to query the status of created migration tasks:

    ``` {#codeblock_36x_zkf_m4g .lanuage-shell}
    aliyun smc DescribeReplicationJobs --JobId j-2ze33rsym********srq
    ```


## Use OpenAPI Explorer to call the SMC API {#section_q7t_0pa_snq .section}

This example uses OpenAPI Explorer to call the operation to create a migration task. Before calling the operation, read the instructions in the API documentation and query the values of required request parameters. If an error occurs during API calling, you can view troubleshooting suggestions in the corresponding API documentation.

To call the operation from Alibaba Cloud CLI, perform the following steps:

1.  Call the [DescribeSourceServers](https://pre-api.aliyun.com/#/?product=smc&api=DescribeSourceServers&tab=DEMO&lang=JAVA) operation to obtain the IDs of migration sources.
2.  Call the [CreateReplicationJob](https://api.aliyun.com/#/?product=smc&api=CreateReplicationJob&tab=DEMO&lang=JAVA) operation to create a migration task.
3.  Call the [DescribeReplicationJobs](https://api.aliyun.com/#/?product=smc&api=DescribeReplicationJobs&tab=DEMO&lang=JAVA) operation to query the status of created migration tasks.

For more information about the SMC API, see [List of operations by function](reseller.en-US/API Reference/List of operations by function.md#).

## Use Java SDK to call the SMC API {#section_y96_3mb_ped .section}

This example uses Java SDK to call the operation to create a migration task. You can obtain the SMC SDK from [Github Repo Alibaba Cloud](https://github.com/aliyun/aliyun-openapi-java-sdk). Before calling the operation, read the instructions in the API documentation and query the values of required request parameters. If an error occurs during API calling, you can view troubleshooting suggestions in the corresponding API documentation.

**Note:** In the following SDK example, `<AccessKey>` \(your AccessKey ID\), `<AccessSecret>` \(your AccessKey Secret \), `<RegionId>` \(the ID of the target Alibaba Cloud region\), and `<SystemDiskSize>` \(the system disk size of the target Alibaba Cloud ECS instance\) must be specified based on actual needs. For more information, see [Create an AccessKey](../../../../reseller.en-US/General Reference/Create an AccessKey.md#), [Regions and zones](../../../../reseller.en-US/General Reference/Regions and zones.md#), and [Migration task request parameters](reseller.en-US/API Reference/Migration tasks/CreateReplicationJob.md#parameters).

``` {#codeblock_kme_u8z_jg6 .language-java}
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
        request.setSourceId("s-bp1ebo013********1jv");

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

