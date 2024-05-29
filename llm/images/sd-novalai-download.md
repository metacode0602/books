# Stable Diffusion NovelAI模型下载

[原文](https://openai.wiki/author/-GVnTZ1z-qVR)



# 模型描述

该模型为NovelAI泄漏的完整版本，Stable Diffusion WebUI可以直接调用，非常适合二次元风格角色以及场景的绘制，如果您想绘制偏写实之类的风格，可以考虑下载本站的其它模型。

## 安装方法

将模型下载后，将会得到一个名为`****.ckpt`格式的文件，将该文件剪切至你的Stable Diffusion本地安装目录，例如站长在测试时所使用的路径为：`D:\openAI\stable-diffusion-webui\models\Stable-diffusion`，请根据自身请问调整模型存放位置。

## 更新详情

NovelAI的模型为官网泄漏版本，经常适应调试之后，是可以与NovelAI官网所提供的收费在线绘制效果完全一致的，而且Stable Diffusion WebUI可完美兼容NovelAI的模型与风格设置。

## 资源详情

NovelAI模型共计50多G，但其实真正可以用到的仅为一个**7.17GB**的ckpt模型即可，本站所提供的NovelAI模型可适用于图片绘制与训练，另外还有一个pt后缀格式的风格化文件，建议将两个文件下载后直接移动到模型位置即可。

| 名称                  | 大小     | 功能            |
| ------------------- | ------ | ------------- |
| final-pruned.ckpt   | 7.17GB | 基础模型，也可以用来训练。 |
| final-pruned.vae.pt | 784MB  | 可自由选择绘图风格     |

文件详情

## 注意事项

如果您想更改文件名称，例如欲将`final-pruned.ckpt`更改为`openAI.ckpt`，那么另一个文件的名称必须为`openAI.vae.pt`，为了避免不必要的麻烦，请尽量不要尝试更改文件名称。

## 下载地址

[NovalAI](https://www.123pan.com/s/sKd9-LvIc.html)





# LoRA模型下载Part-1

为方便大家学习使用，本站提示大量LoRA模型，以下模型搬自[Civitai官网](https://openai.wiki/go?_=353513c85baHR0cHM6Ly9jaXZpdGFpLmNvbS8%3D)的LORA标签，为保证AI角色的训练原型合法权益，请于下载后的24小时内自行删除，或自行前往官网按需下载，谢谢合作。

本文包括仿宋服、韩国娃娃、约尔·福杰、果冻、张娜英、蠢沫沫、台湾女孩、雷电将军、丁真、玛奇玛、露西、墨心、疏可走马、女牛仔、刘亦菲、SamYang、尤尔哈2B、海保利、BetterBodies、Liyuu、Chilloutmix-Ni、NeverEnding Dream等角色模型下载。

[本站](https://openai.wiki/)之后将会陆续整理热门Lora资源分享给大家，每P大概20个左右。

在下一期将为大家提供茵妮斯、汉服、狗狗风格、鬼刀风格、Lisa、李知恩、艾琳、黄礼志、金智妮、河北彩花、七草荠、阿慈谷日富美、朴彩英、狗头萝莉、元神、甘雨、迪丽热巴、朴智妍、Atdan、WLOP、IU、Irene、Yeji、Jennie、Rosè、Ganyu、Dilraba、Jiyeon等模型。

## ## 前置条件

本面模型需要您在本地安装并部署Stable Diffusion WebUI，可以通过阅读下面的文章进行安装部署。

除SD之外，您还需要会使用LoRA，以下是关于LoRA的使用教程，以及相关资源下载。

## 基础模型

基础模型可以理解为一栋大楼的地基，是这一整栋大楼的根本，如果没有地基的存在，也就没有办法在上面建设每个单独的房间。

所以如果你想使用Lora生成指定的角色，那就必须要先加载基础模型，然后再安装角色模型。

| 名称                      | 中文名称    | 大小     | 网盘                                                                                            |
| ----------------------- | ------- | ------ | --------------------------------------------------------------------------------------------- |
| Chilloutmix-Ni          | 清凉组合    | 7.17GB | [下载](https://openai.wiki/go?_=0e7e2ad381aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktTGtKYy5odG1s) |
| NeverEnding Dream (NED) | 永无止境的梦想 | 3.97GB | [下载](https://openai.wiki/go?_=ee7cbe53dfaHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktYjRKYy5odG1s) |

## 角色模型

为尊重原作者权益，您下载后必须在24小时之内删除，如果您喜欢某个模型，请另行前往官方地址下载。

| 名称                         | 中文名称    | 角色标签                                          | 网盘                                                                                            |
| -------------------------- | ------- | --------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Yae Miko                   | 八重神子    | <lora:yaeMikoRealistic_yaemikoFull:1>         | [下载](https://openai.wiki/go?_=a220cc6853aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktZWtKYy5odG1s) |
| Korean Doll                | 韩国娃娃    | <lora:koreanDollLikeness_v15:0.66>            | [下载](https://openai.wiki/go?_=177722515daHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktY2tKYy5odG1s) |
| Yor Briar                  | 约尔·福杰   | <lora:yor:0.6>                                | [下载](https://openai.wiki/go?_=0fc8368d0eaHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktNWtKYy5odG1s) |
| Jelly                      | 果冻      | <lora:niji_jelly:0.7>                         | [下载](https://openai.wiki/go?_=12015da716aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktNmtKYy5odG1s) |
| i_am_young22               | 张娜英     | <lora:zny_1.0:0.7>                            | [下载](https://openai.wiki/go?_=55604a369baHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktamtKYy5odG1s) |
| chunmomo                   | 蠢沫沫     | <lora:chunmm:0.8>                             | [下载](https://openai.wiki/go?_=4dc78ab279aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktVG9KYy5odG1s) |
| Taiwan Doll                | 台湾女孩    | <lora:taiwanDollLikeness_v10:0.66>            | [下载](https://openai.wiki/go?_=f8b4273e9daHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktZG9KYy5odG1s) |
| Raiden Shogun              | 雷电将军    | <lora:raidenShogunRealistic_raidenshogun:0.6> | [下载](https://openai.wiki/go?_=627ddf637aaHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktM29KYy5odG1s) |
| hf2ming-beta-020601        | 仿宋服风格   | <lora:hf2ming-beta-020601:1>                  | [下载](https://openai.wiki/go?_=38e21cf8d5aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktQXhKYy5odG1s) |
| DingZhenLora               | 丁真      | <lora:DingZhenLora:1>                         | [下载](https://openai.wiki/go?_=de409320aeaHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktbDRKYy5odG1s) |
| Makima (Chainsaw Man) LoRA | 玛奇玛     | <lora:makima_offset:1>                        | [下载](https://openai.wiki/go?_=5ee485f95faHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktWjRKYy5odG1s) |
| Lucy                       | 露西      | <lora:lucy-000035:0.7>                        | [下载](https://openai.wiki/go?_=a677937db2aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktYzRKYy5odG1s) |
| MoXin                      | 墨心      | <lora:Moxin_1010:1>                           | [下载](https://openai.wiki/go?_=f1bfc8bcf1aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktZTRKYy5odG1s) |
| Shukezouma                 | 疏可走马    | <lora:Moxin_Shukezouma:0.7>                   | [下载](https://openai.wiki/go?_=4ab72672ffaHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktdDRKYy5odG1s) |
| POV Squatting Cowgirl LoRA | 女牛仔     | <lora:PSCowgirl:0.9>                          | [下载](https://openai.wiki/go?_=35ecc4fafaaHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktejRKYy5odG1s) |
| LiuYiFei                   | 刘亦菲     | <lora:liuyifei_10:0.8>                        | [下载](https://openai.wiki/go?_=dd8eab3293aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktTDRKYy5odG1s) |
| Sam Yang Style LoRA        | SamYang | <lora:sam_yang_offset:1>                      | [下载](https://openai.wiki/go?_=d56b52ae7faHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktNTRKYy5odG1s) |
| YoRHa No. 2 Type B         | 尤尔哈2B   | <lora:yorha_noDOT_2_type_b:0.5>               | [下载](https://openai.wiki/go?_=ba07c872c4aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktNjRKYy5odG1s) |
| Hipoly 3D Model LoRA       | 海保利     | <lora:hipoly3DModelLora_v10:0.5>              | [下载](https://openai.wiki/go?_=dbc744e9f3aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDkteTRKYy5odG1s) |
| Better Bodies              | 更好的身体   | <lora:breastInClass:1>                        | [下载](https://openai.wiki/go?_=51c2e592f0aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktVjRKYy5odG1s) |
| Liyuu LoRA                 | リーユウ    | <lora:Liyuu:0.8>                              | [下载](https://openai.wiki/go?_=9f6ed47153aHR0cHM6Ly93d3cuMTIzcGFuLmNvbS9zL3NLZDktVHhKYy5odG1s) |


