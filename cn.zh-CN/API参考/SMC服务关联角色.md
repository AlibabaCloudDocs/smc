# SMC服务关联角色

本文主要介绍SMC服务关联角色（AliyunServiceRoleForSMC）以及如何删除SMC服务关联角色。

## 背景信息

SMC服务关联角色（AliyunServiceRoleForSMC）是访问控制提供的一种服务关联角色。更多信息，请参见[服务关联角色](/cn.zh-CN/角色管理/服务关联角色.md)。在导入迁移源时，SMC会自动创建AliyunServiceRoleForSMC。当执行迁移任务时，SMC将通过AliyunServiceRoleForSMC获取云服务器ECS的访问权限。

## AliyunServiceRoleForSMC说明

-   角色名称：AliyunServiceRoleForSMC
-   角色权限策略：AliyunServiceRoleForSMC
-   权限说明：

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


## 删除SMC服务关联角色

您可以手动删除AliyunServiceRoleForSMC，删除后SMC将不再获取云服务器ECS的访问权限。在删除前，请先通过以下任一方式删除依赖SMC服务关联角色的迁移源。

-   登录[SMC控制台](https://smc.console.aliyun.com/)，在左侧导航栏单击**迁移源**，找到要删除的迁移源进行手动删除。
-   调用[DeleteSourceServer](/cn.zh-CN/API参考/迁移源/DeleteSourceServer.md)删除迁移源。

迁移源成功删除后，可以删除SMC服务关联角色。具体操作，请参见[删除RAM角色](/cn.zh-CN/角色管理/删除RAM角色.md)。

