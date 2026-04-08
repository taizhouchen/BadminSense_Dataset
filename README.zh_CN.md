# BadminSense_Dataset [ 简体中文 | [English](./README.md) ]


本仓库包含论文[《BadminSense:Enabling Fine-Grained Badminton Stroke Evaluation on
a Single Smartwatch》]() 所构建的数据集。我们的工作能够通过佩戴单一智能手表捕获人体羽毛球运动数据，并支持即时的细颗粒度运动分析和长期的运动表现跟踪与数据统计。

![System Overview](.assets/teaser_sub.png)

## Licenses
<a rel="license" href="https://creativecommons.org/licenses/by-nc-nd/4.0/"><img alt="Creative Commons License" style="border-width:0" src="https://licensebuttons.net/l/by-nc-nd/4.0/88x31.png" /></a><br />
本作品采用 <a rel="license" href="https://creativecommons.org/licenses/by-nc-nd/4.0/">Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License</a> 授权。

 所有材料均采用 [Creative Commons BY-NC-ND 4.0](https://creativecommons.org/licenses/by-nc-nd/4.0/legalcode) 许可协议发布。
 您可以为**非商业目的下载、使用和分享**这些材料，但请通过**适当注明引用我们的论文**，且**不得以任何方式修改或用于商业用途**。

## BADS_CLL Dataset

BadminSense 构建了名为 BADS_CLL 的羽毛球运动数据集，包含四种常用击球动作的击球类型标签，手动标记的球拍击球点位置，以及资深羽毛球球员对击球动作质量的评估分数。

![Dataset Overview](.assets/dataset_sub.png)

### Download

您可以从 Google Drive 下载数据集（14 GB, 版本 1.0） [[BADS_CLL_OPENACCESS_V1](https://drive.google.com/file/d/10Jp0-fqgbI4Gg4-hmDnopFc3JdQNQOnc/view?usp=sharing)]。BADS_CLL 数据集包含 848 个有效击球样例，每个样例提供传感器（IMU+音频）运动数据，运动视频片段，球员信息，以及 `Stroke Type`，`Stroke Quality Rating`，`Impact Location` 共三个数据标签。

### Data Format and Description

> Overall Format

在解压下载的 `.zip` 文件后，您将会得到由 96 个文件夹构成的 BADS_CLL 数据集。每个文件夹对应一位 Player 一种 `Stroke Type` 的一个`Section`，包含至多 10 个有效击球动作的相关数据。

此外，文件夹名称 RecordName 记录了一定的信息，格式为 `Gender_Exp_StrokeType_PlayerCode_Section_Device`。您可以据此通过文件夹名称快速了解该 `Section` 的大致信息。

> Section Format

当打开一个文件夹，即一个 `Section` 后，您将会得到一个包含至多 10 个有效击球动作数据 `.json` 文件，以及与每个动作数据对应的击球 `.gif` 文件。

对于一个有效击球动作，其数据主要由 `Info`，`Label`，`Data`，和 `Gif` 组成，具体内容如下：

* `Info`

|Field|Description|
|-|-|
|recordName|与文件夹名称相同|
|gender|Player 的性别（Man, Women）|
|exp|Player 的羽毛球运动经验（Low, Medium, High）|
|section|该 `Stroke Type` 的第（1, 2）个 `Section`|
|device|Play 佩戴的智能手表尺寸（'1': 48mm, '2': 42mm）|
|startTimestamp|该击球动作的起始时间戳|
|endTimestamp|该击球动作的结束时间戳|

* `Label`

|Field|Description|
|-|-|
|positionX|`Impact Location` x 坐标 [-1, 1]|
|positionY|`Impact Location` y 坐标 [0, 1]|
|actionType|`Stroke Type`|
|actionEval|7 位资深球员给出的 `Stroke Quality Rating`|

数据集击球类型与论文击球类型对应关系如下：

|Dataset|Paper|
|:-:|:-:|
|BackhandTransition|BOC|
|ForehandHigh|FOC|
|ForehandLob|FOD|
|ForehandKill|FOS|

* `Data`

|Field|Description|
|-|-|
|ACCELEROMETER|加速度计 xyz data 与 timestamp|
|AUDIO|麦克风 data 与 timestamp|
|GYROSCOPE|陀螺仪 xyz data 与 timestamp|
|GYROSCOPE_UNCALIBRATED|陀螺仪未校准 xyz data，drift，与 timestamp|
|MAGNETIC_FIELD|磁力计 xyz data 与 timestamp|
|MAGNETIC_FIELD_UNCALIBRATED|磁力计未校准 xyz data，Bias，与 timestamp|
|ROTATION_VECTOR|旋转矢量 xyz data，cos delta， heading accuracy， 与 timestamp|

其中，IMU 数据采样率为 100Hz，麦克风数据采样率为 16000Hz。

* `Gif`

`.gif` 文件的命名格式为 `recordName@Index.gif`，其中 `Index` 为对应击球动作数据在 `.json` 的次序，从 0 开始计数。

## Citation

如果您觉得我们的论文或材料有用，请考虑引用：

```latex

```
