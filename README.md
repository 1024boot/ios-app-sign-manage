<p align="center">
<img src="https://user-images.githubusercontent.com/99250217/192147461-f799305b-d876-45dc-bc32-6d73672dec75.png"/>
</p>

# 尼卡应用签名管理工具
- 官网：https://nikaap.com
- QQ技术客服：[1502717003](http://wpa.qq.com/msgrd?v=3&uin=1502717003&site=qq&menu=yes)
- QQ群：305947680
- 邮箱：nika@nikaap.com

写在前面：<br>
**FYI**<br>
**尼卡签名管理不会要求用户导出证书或让用户设置本地证书所在目录，而是直接安全读取本地钥匙串证书列表，由于macOS系统限制，读取钥匙串证书列表只能拿到证书的名字和SHA-1值，并不能获取到证书的私钥。所有要求上传证书或者需要用户设置导出证书的所在目录都是有风险的行为**

本文中附邀请码注册优惠

---
# 介绍
## 主要使用场景
企业证书签名的应用可以不通过App Store自行的进行分发，通过下载链接提供给其他人下载，使用。但是如果对使用的数量和使用的频次不加以控制很容易会导致企业证书被封无法使用。
## 尼卡签名功能
使用尼卡签名可以控制每个应用的总安装使用限量、每日安装使用限量、以及应用使用的时长等。一般场景：
- 自行分发使用：如果不加以控制，应用可能被很多人下载使用，苹果发现证书使用异常会立刻封禁企业证书。如果使用尼卡签名管理，可以设置应用使用的总数量，如果达到总数量后应用会无法使用发生闪退。这样可以有效保护企业证书。
- 提供签名服务给软件提供者：除去上述的控制外，还可以控制应用使用的时长来进行管理。应用如果达到有效期后将不可使用，这时可用通过尼卡签名设置自定义的到期弹窗提示使用者使用期限已到。如果不设置提醒弹窗，到期后应用打开自动闪退。有效期可以在管理界面随时更改。

**上述的所有设置可以在应用管理界面更改实时生效，不需要再次签名。**

尼卡签名管理还可以注入开发者自行开发的动态库，修改Bundle ID、应用名称、应用版本等信息，签名时可更改的应用信息如下：

![image](https://user-images.githubusercontent.com/99250217/192142683-b80ad846-f220-407b-893b-dc471955178b.png)

# 使用
## 签名界面
![image](https://user-images.githubusercontent.com/99250217/192143437-88a60771-956a-4eec-8e62-20e3539300e3.png)

签名界面填入：
- 签名文件：需要重签名的包所在目录
- 描述文件：描述文件所在目录
- 签名证书：如果钥匙串有证书会自动读取钥匙串的证书列表，如果没有需要将证书安装在钥匙串里然后点击刷新

再次声明：
**尼卡签名管理不会要求用户导出证书或让用户设置本地证书所在目录，而是直接安全读取本地钥匙串证书列表，由于macOS系统限制，读取钥匙串证书列表只能拿到证书的名字和SHA-1值，并不能获取到证书的私钥。**

其他配置项都是可选的，具体每个配置项的含义可以将鼠标悬停在 **?** 上查看。<br>
必填项的三项选好后点击 **开始签名** 进行签名。签名成功后应用相关信息会出现在 **应用管理** 中，签名后应用ipa文件与签名文件在同一目录下。可以在签名设置中设置 **签名成功后打开文件夹**

## 应用管理
![image](https://user-images.githubusercontent.com/99250217/192144040-020a479f-9cec-40aa-b9b2-6988bbe3f803.png)

点击应用列表里的任何一个应用，界面右侧会出详细的应用信息。鼠标右键点击应用所在行或者在点击应用详细信息底部的编辑，可以设置应用相关控制的信息，实时生效。

![image](https://user-images.githubusercontent.com/99250217/192144704-eea28ad5-670c-4596-a689-7fb7eb512697.png)

设置项说明
- 开启/关闭应用：关闭应用后应用将无法使用，应用启动立即闪退，开启应用后恢复正常。
- 修改安装限量：允许安装应用使用的最大限量，默认1000，表示使用应用达到1000个设备后，其他设备将无法使用。
- 修改应用到期时间：应用到有效期后将闪退或者弹窗提示，用户无法使用。
- 关闭到期时间：应用无使用时间限制。
- 开启/关闭到期弹窗：关闭后应用到期后闪退，开启后应用到期后弹窗提醒。
- 修改到期弹窗提示语：应用到期后弹窗显示的到期提示语。
- 安装总量清零：重新统计安装总量。
- 修改每日安装限量：设置每日允许安装的总量，更准确的控制安装数量，如果设置为0表示每日安装不限量。
- 修改备注：一些备注信息。
- 删除应用：如果应用删除后，用户将无法使用，打开应用后立刻闪退。

## 签名设置
![image](https://user-images.githubusercontent.com/99250217/192145124-33c848d6-ccd3-44df-baff-230d346e63ac.png)
应用签名的默认值，如果签名时不额外设置以签名设置里为准，具体每个配置项的含义可以将鼠标悬停在 **?** 上查看。

## 账户与套餐
![image](https://user-images.githubusercontent.com/99250217/192145342-605a32ac-a350-4abd-bd11-f7edc3918c60.png)
目前有四种套餐：
- 应用管理额度【10】
- 应用管理额度【20】
- 应用管理额度【50】
- 应用管理额度【1000】

- 优惠信息
  - 普通注册用户首次充值会有优惠
  - 使用邀请码注册的用户会有优惠（优惠力度更大）

**邀请码：5PO9YZ** 

注：所有优惠都仅限首次充值

## 安装应用
![image](https://user-images.githubusercontent.com/99250217/192145745-912875c0-b75b-4b43-845c-05bb8d230294.png)
手机连接到电脑上并信任后将应用拖拽到虚线框后即可安装，点击底部的重置按钮后可以再次拖拽安装。

# 常见问题
### 为什么软件下载后无法安装打开？<br>
由于苹果官方不建议对应用进行重签名，所以对重签名工具有安装限制，按照如下方法打开应用<br>
方法一：
- 点按“安全性与隐私”偏好设置中“通用”面板上的“仍要打开”按钮来允许被阻止的 App。此按钮在您尝试打开该 App 后一小时内可用。

方法二：
  1. 在 Mac 上的“访达” 中，找到想要打开的 App。
  2. 按住 Control 键点按 App 图标，然后从快捷键菜单中选取“打开”。
  3. 点按“打开”。
### 签名证书和配置描述文件如何获取？
签名证书和配置描述文件可以通过苹果开发者账号后台配置生成，也可以直接通过其他人钥匙串导出的P12文件和描述文件。
### 签名后的APP可以直接安装到手机上吗？
- 安装到自己的手机：将手机连接到电脑上并信任，在尼卡签名管理-安装应用中将ipa包拖拽到虚线框内即可完成安装
- 安装到其他人手机上：传到类似蒲公英这样的分发平台通过网页形式安装，以个人或公司证书签名的需要先将待安装设备的UDID添加到描述文件，企业证书则不需要，可以任意安装到手机。
### 第三方动态库（.dylib）如何获取？
第三方库动态库文件需要对应技术人员开发，通过编写相关的代码，最后注入到IPA包中，在APP运行时执行相应的功能，如需要此方面功能，可联系我们技术开发人员咨询相关问题。

### 签名后一直显示没有激活是怎么回事？
如果手机已安装运行了APP，但是软件记录刷新后仍然没有激活，可能是签名过程出现错误，大多情况是因为ipa包比较大，比如超过2G，或包mach-o文件名称不规则等，这时候需要联系我们技术客服，排查原因，协助签名。

### 签名总失败是为什么？
整个签名流程分成有很多步骤，包括但不限于账户状态检测，动态库是否注入成功等，具体问题需要联系我们技术客服进行排查。

### 为什么签名成功的应用无法安装？
1. 如果重签名的应用是从App Store上下载的，那么可能这个应用没有脱壳，导致安装失败。
2. 安装的应用在手机上存在App Store下载的相同应用，这时需要签名时更改bundleID或者卸载本机相同的应用，重新安装。

### 套餐到期后如何处理已经签名过的APP？
套餐到期后所有应用都会停用，无法使用。
