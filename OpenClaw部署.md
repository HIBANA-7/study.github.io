Agent:OpenClaw
安装位置：D:\software\openclaw
前置要求：需要先安装 Nobe.js（版本 >= 22)  和 Git Bash

第一步：创建工作区目录
#手动或者通过mkdir命令都可以
mkdir D:\software\openclaw\workspace

第二步：配置环境变量
确保 OpenClaw 按指定的目录生成相关的配置文件和数据目录。
2.1 设置系统环境变量
1.按 win+R键，输入sysdm.cpl并回车
2.高级选项卡
3.环境变量
2.2添加用户环境变量
变量 1：OPENCLAW_HOME
变量值 D:\software\openclaw
变量 2：OPENCLAW_WORKSPACE
变量值 D:\software\openclaw\workspace
变量 3：OPENCLAW_CONFIG_PATH
变量值 D:\software\openclaw\openclaw.json
变量 4：OPENCLAW_STATE_DIR
变量值 D:\software\openclaw

2 .3验证环境变量
关闭并重新打开Git Bash，验证环境变量是否生效。
echo $OPENCLAW_HOME
echo $OPENCLAW_WORKSPACE
echo $OPENCLAW_CONFIG_PATH
echo $OPENCLAW_STATE_DIR
如果生效会显示刚刚设置的路径。

第三步：安装OpenClaw
npm install -g openclaw

第四步：运行配置向导
使用 openclaw onboard 命令启动交互式配置向导：
openclaw onboard --workspace D:\software\openclaw\workspace --install-daemon
4.1配置步骤 1：确认安装
向导启动后，第一个配置界面默认选择 Yes，直接按回车继续。

4.2配置步骤 2：选择配置模式
选择 QuickStart 快速开始模式，按回车继续。
4.3配置步骤 3：选择 AI 模型
我这里暂时选用NVIDIA免费API。
4.4配置步骤 4：配置 API Key
4.5配置步骤 5：选择聊天平台
我暂时选择的是飞书，需要在飞书开放平台创建应用来获取配置飞书应用的 App Secret 和 App ID。

第五步：验证安装
5.1 检查版本
openclaw --version

5.2 打开桌面网页访问
1先找到桌面网页访问的地址 一般默认是127.0.0.1:18789, 端口如果在配置时修改过，找到openclaw工作目录下的openclaw.json文件中查看gateway配置即可：
"gateway": {
    "mode": "local",
    "auth": {
      "mode": "token",
      "token": "a3de353f95aa32095c63994bf70a867c717c49f8e067dd25"
    },
浏览器访问127.0.0.1:18789 默认会出现一个登录页面，我们只需要在网关令牌输入框填入5.2中配置文件的token的值，然后点击登录即可

第六步：飞书配对
6.1 打开飞书
在飞书中找到对应的应用。
6.2 发送测试消息
打开手机飞书，搜索应用（配置步骤6中创建的应用名称），在飞书聊天窗口发送任意文字，获取配对代码
6.3 完成配对
根据手机飞书回复的向导提示，在电脑桌面cmd命令行输入配对代码，完成配对
openclaw pairing approve feishu CUXNXVPM

6.4 验证是否配对成功
回到手机飞书聊天窗口，发送任意文字，如果有回复就代表配对成功

总结
完整安装流程：
# 1. 创建工作区
mkdir D:\software\openclaw\workspace

# 2. 配置环境变量
# OPENCLAW_HOME = D:\software\openclaw
# OPENCLAW_WORKSPACE = D:\software\openclaw\workspace
# OPENCLAW_CONFIG_PATH = D:\software\openclaw\config
# OPENCLAW_STATE_DIR = D:\software\openclaw\state

# 3. 安装 OpenClaw
npm install -g openclaw

# 4. 运行配置向导（指定工作区）
openclaw onboard --workspace D:\software\openclaw\workspace --install-daemon

# 5. 验证安装
openclaw --version

# 6.飞书配对
