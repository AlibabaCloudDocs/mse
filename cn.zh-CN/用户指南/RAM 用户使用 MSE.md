# RAM 用户使用 MSE {#concept_1425955 .concept}

MSE 支持云账户（主账号）给 RAM 用户（子账号）授予 MSE 的操作权限，避免因暴露阿里云账号（主账号）密钥造成的安全风险。本文介绍如何创建 RAM 用户并给 RAM 用户授权，授权后您就可以通过 RAM 用户使用 MSE。

## 操作步骤 {#section_9sl_5qz_9lo .section}

1.  使用云账号（主账号）创建 RAM 用户。详情请参见[创建RAM用户](../../../../../cn.zh-CN/用户指南/用户/创建RAM用户.md#)。
2.  使用云账号（主账号）为新建的 RAM 用户授权。详情请参见[为RAM用户授权](../../../../../cn.zh-CN/用户指南/用户/为RAM用户授权.md#)。

    根据实际需求，可以为 RAM 用户授权两种权限：

    -   AliyunMSEFullAccess 权限
    -   AliyunMSEReadOnlyAccess 权限

## 结果验证 {#section_s6o_r0k_wl7 .section}

RAM 用户创建并授权完成后，使用 RAM 用户登录 MSE。可以正常使用 MSE。

