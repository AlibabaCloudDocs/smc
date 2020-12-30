# Service linked roles for SMC

This topic describes the AliyunServiceRoleForSMC service linked role for Server Migration Center \(SMC\). It also describes how to delete the role.

## Background information

Resource Access Management \(RAM\) provides a service linked role named AliyunServiceRoleForSMC for SMC. For more information, see [Service linked roles](/intl.en-US/RAM Role Management/Service linked roles.md). When a migration source is imported, SMC creates a service linked role named AliyunServiceRoleForSMC. During a migration task, SMC uses the AliyunServiceRoleForSMC service linked role to access Elastic Compute Service \(ECS\) instances.

## AliyunServiceRoleForSMC

-   Role name: AliyunServiceRoleForSMC
-   Policy name: AliyunServiceRoleForSMC
-   The policy specifies the following permissions:

    ```
    {
      "Version": "1",
      "Statement": [
        {
          "Action": [
            "ecs:DescribeAvailableResource",
            "ecs:DescribeZones",
            "ecs:RunInstances",
            "ecs:DescribeInstances",
            "ecs:StopInstance",
            "ecs:DeleteInstance",
            "ecs:AuthorizeSecurityGroup",
            "ecs:DescribeSecurityGroupAttribute",
            "ecs:CreateSecurityGroup",
            "ecs:DeleteSecurityGroup",
            "ecs:DescribeSecurityGroups",
            "ecs:CreateSnapshot",
            "ecs:DeleteSnapshot",
            "ecs:DescribeSnapshots",
            "ecs:CreateImage",
            "ecs:DescribeImages",
            "ecs:DescribeDisks",
            "ecs:DescribeAccountAttributes",
            "ecs:StartInstance",
            "ecs:DeleteImage",
            "ecs:DescribeLaunchTemplates",
            "ecs:DescribeLaunchTemplateVersions",
            "ecs:DescribeKeyPairs",
            "ecs:DetachDisk",
            "ecs:ReplaceSystemDisk",
            "ecs:AttachDisk",
            "ecs:DeleteDisk"
          ],
          "Resource": "*",
          "Effect": "Allow"
        },
        {
          "Action": [
            "vpc:CreateVpc",
            "vpc:CreateVSwitch",
            "vpc:DescribeVpcs",
            "vpc:DeleteVSwitch",
            "vpc:DeleteVpc",
            "vpc:DescribeVSwitches"
          ],
          "Resource": "*",
          "Effect": "Allow"
        },
        {
          "Action": [
            "ram:GetRole",
            "cr:GetRepository"
          ],
          "Resource": "*",
          "Effect": "Allow"
        },
        {
          "Action": "ram:PassRole",
          "Resource": "*",
          "Effect": "Allow",
          "Condition": {
            "StringEquals": {
              "acs:Service": [
                "ecs.aliyuncs.com"
              ]
            }
          }
        },
        {
          "Action": "ram:DeleteServiceLinkedRole",
          "Resource": "*",
          "Effect": "Allow",
          "Condition": {
            "StringEquals": {
              "ram:ServiceName": "smc.aliyuncs.com"
            }
          }
        }
      ]
    }
    ```


## Delete the service linked role for SMC

You can manually delete the AliyunServiceRoleForSMC service linked role. After it is deleted, SMC no longer obtains permissions to access ECS resources. Before you delete the AliyunServiceRoleForSMC service linked role, you must use one of the following methods to delete the migration source that is associated with the role.

-   Log on to the [Server Migration Center console](https://smc.console.aliyun.com/). In the left-side navigation pane, click **Migration Sources**. On the Migration Sources page, delete the migration source that you want to delete.
-   Call the [DeleteSourceServer](/intl.en-US/API Reference/Migration sources/DeleteSourceServer.md) operation to delete the migration source.

After the migration source is deleted, you can delete the associated service linked role. For more information, see [Delete a RAM role](/intl.en-US/RAM Role Management/Delete a RAM role.md).

