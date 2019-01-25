# kaggle_liveoffice01

```
此竞赛的目标是根据该计算机的不同属性预测Windows计算机被各种恶意软件系列感染的可能性。包含这些属性和机器感染的遥测数据是通过组合Microsoft端点保护解决方案Windows Defender收集的心跳和威胁报告生成的。

此数据集中的每一行对应一台机器，由a唯一标识MachineIdentifier。HasDetections是事实并且表明在机器上检测到恶意软件。使用中的信息和标签train.csv，您必须预测HasDetections每台机器的值test.csv。

用于创建此数据集的抽样方法旨在满足某些业务约束，包括用户隐私以及计算机运行的时间段。恶意软件检测本质上是一个时间序列问题，但由于引入了新机器，在线和离线的机器，接收补丁的机器，接收新操作系统的机器等，它变得复杂。虽然此处提供的数据集已经过大致按时间划分，上述并发症和抽样要求可能意味着您可能会发现您的交叉验证，公共和私人分数之间存在不完美的一致性！此外，该数据集并不代表微软客户的机器; 它已被抽样以包含更大比例的恶意软件机器。

列
不可用或自我记录的列名称标有“NA”。

MachineIdentifier - 个人机器ID
ProductName - 后卫状态信息，例如win8defender
EngineVersion - 后卫状态信息，例如1.1.12603.0
AppVersion - 后卫状态信息，例如4.9.10586.0
AvSigVersion - 后卫状态信息，例如1.217.1014.0
IsBeta - 后卫状态信息，例如假
RtpStateBitfield - NA
IsSxsPassiveMode - NA
DefaultBrowsersIdentifier - 机器默认浏览器的ID
AVProductStatesIdentifier - 用户防病毒软件的特定配置的ID
AVProductsInstalled - NA
AVProductsEnabled - NA
HasTpm - 如果机器有tpm，则为真
CountryIdentifier - 机器所在国家/地区的ID
CityIdentifier - 机器所在城市的ID
OrganizationIdentifier - 机器所属组织的ID，组织ID映射到特定公司和广泛行业
GeoNameIdentifier - 计算机所在地理区域的ID
LocaleEnglishNameIdentifier - 当前用户的Locale ID的英文名称
Platform - 计算平台名称（OS相关属性和处理器属性）
Processor - 这是已安装操作系统的过程体系结构
OsVer - 当前操作系统的版本
OsBuild - 构建当前的操作系统
OsSuite - 当前操作系统的产品套件掩码。
OsPlatformSubRelease - 返回OS平台子版本（Windows Vista，Windows 7，Windows 8，TH1，TH2）
OsBuildLab - 构建生成当前操作系统的实验室。示例：9600.17630.amd64fre.winblue_r7.150109-2022
SkuEdition - 此功能的目标是使用MSDN中定义的产品类型映射到在人口报告中有用的“SKU-Edition”名称。有效的产品类型在％sdxroot％\ data \ windowseditions.xml中定义。自Vista和Server 2008以来一直使用此API，因此有许多产品类型不适用于Windows 10.“SKU-Edition”是一个字符串值，属于三类结果之一。设计必须交给每个班级。
IsProtected - 这是一个源自Spynet Report的AV产品领域的计算字段。返回：a。如果此计算机上至少有一个活动的和最新的防病毒产品正在运行，则为TRUE。湾 如果此计算机上没有活动的AV产品，或者AV处于活动状态但未收到最新更新，则为FALSE。C。如果报告中没有防病毒产品，则返回null。返回：机器是否受保护。
AutoSampleOptIn - 这是从服务传入的SubmitSamplesConsent值，可在CAMP 9+上获得
PuaMode - 来自服务的Pua Enabled模式
SMode - 当已知设备处于“S模式”时，此字段设置为true，如Windows 10 S模式，其中只能安装Microsoft Store应用程序
IeVerIdentifier - NA
SmartScreen - 这是注册表中启用SmartScreen的字符串值。这是通过按顺序检查HKLM \ SOFTWARE \ Policies \ Microsoft \ Windows \ System \ SmartScreenEnabled和HKLM \ SOFTWARE \ Microsoft \ Windows \ CurrentVersion \ Explorer \ SmartScreenEnabled获得的。如果值存在但为空白，则在遥测中发送值“ExistsNotSet”。
Firewall - 如果服务报告启用了Windows防火墙，则此属性对于Windows 8.1及更高版本为true（1）。
UacLuaenable - 此属性报告是否在UAC中禁用或启用了“管理员批准模式中的管理员”用户类型。报告的值是通过读取regkey HKLM \ SOFTWARE \ Microsoft \ Windows \ CurrentVersion \ Policies \ System \ EnableLUA获得的。
Census_MDC2FormFactor - 基于设备普查级别硬件特征组合的分组。用于定义Form Factor的逻辑植根于商业和行业标准，并与人们对其设备的思考方式保持一致。（例如：智能手机，小平板电脑，一体机，可转换......）
Census_DeviceFamily - AKA DeviceClass。表示操作系统版本的设备类型。示例值：Windows.Desktop，Windows.Mobile和iOS.Phone
Census_OEMNameIdentifier - NA
Census_OEMModelIdentifier - NA
Census_ProcessorCoreCount - 处理器中的逻辑核心数
Census_ProcessorManufacturerIdentifier - NA
Census_ProcessorModelIdentifier - NA
Census_ProcessorClass - 处理器分为高/中/低。最初用于定价等级SKU。不再维护和更新
Census_PrimaryDiskTotalCapacity - 机器主磁盘上的磁盘空间量（MB）
Census_PrimaryDiskTypeName - 主磁盘类型的友好名称 - HDD或SSD
Census_SystemVolumeTotalCapacity - 以MB为单位安装系统卷的分区大小
Census_HasOpticalDiskDrive - True表示机器有光盘驱动器（CD / DVD）
Census_TotalPhysicalRAM - 以MB为单位检索物理RAM
Census_ChassisTypeName - 检索机器具有哪种机箱类型的数字表示。值0表示xx
Census_InternalPrimaryDiagonalDisplaySizeInInches - 检索主显示屏的物理对角线长度（以英寸为单位）
Census_InternalPrimaryDisplayResolutionHorizontal - 检索内部显示器水平方向的像素数。
Census_InternalPrimaryDisplayResolutionVertical - 检索内部显示屏垂直方向的像素数
Census_PowerPlatformRoleName - 表示OEM首选电源管理配置文件。此值有助于识别设备的基本形状因子
Census_InternalBatteryType - NA
Census_InternalBatteryNumberOfCharges - NA
Census_OSVersion - 数字操作系统版本示例 - 10.0.10130.0
Census_OSArchitecture - 操作系统所基于的架构。源自OSVersionFull。示例 - amd64
Census_OSBranch - 从OsVersionFull中提取的OS分支。示例 - OsBranch = fbl_partner_eeap，其中OsVersion = 6.4.9813.0.amd64fre.fbl_partner_eeap.140810-0005
Census_OSBuildNumber - 从OsVersionFull中提取的OS内部版本号。示例 - OsBuildNumber = 10512或10240
Census_OSBuildRevision - 从OsVersionFull中提取的OS Build修订版。示例 - OsBuildRevision = 1000或16458
Census_OSEdition - 当前操作系统的版本。源自注册表中的HKLM \ Software \ Microsoft \ Windows NT \ CurrentVersion @ EditionID。示例：企业
Census_OSSkuName - OS版友好名称（目前仅限Windows）
Census_OSInstallTypeName - 友好的描述机器上使用的安装，即清洁
Census_OSInstallLanguageIdentifier - NA
Census_OSUILocaleIdentifier - NA
Census_OSWUAutoUpdateOptionsName - 计算机上WindowsUpdate自动更新设置的友好名称。
Census_IsPortableOperatingSystem - 表示操作系统是否通过USB记忆棒上的Windows-To-Go启动并运行。
Census_GenuineStateName - OSGenuineStateID的友好名称。0 =正版
Census_ActivationChannel - 机器的零售许可证密钥或批量许可证密钥。
Census_IsFlightingInternal - NA
Census_IsFlightsDisabled - 指示机器是否参与飞行。
Census_FlightRing - 设备用户希望接收航班的响铃。这可能与当前安装的OS的环不同，如果用户在从不同的环获得航班后更改了环。
Census_ThresholdOptIn - NA
Census_FirmwareManufacturerIdentifier - NA
Census_FirmwareVersionIdentifier - NA
Census_IsSecureBootEnabled - 表示是否启用了安全启动模式。
Census_IsWIMBootEnabled - NA
Census_IsVirtualDevice - 识别虚拟机（机器学习模型）
Census_IsTouchEnabled - 这是触控设备吗？
Census_IsPenCapable - 设备是否能够输入笔？
Census_IsAlwaysOnAlwaysConnectedCapable - 检索有关电池是否使设备始终为AlwaysOnAlwaysConnected的信息。
Wdft_IsGamer - 根据硬件组合指示设备是否为游戏玩家设备。
Wdft_RegionIdentifier - NA
```
