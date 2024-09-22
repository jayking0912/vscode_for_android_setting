

# 🎉 vscode_for_android_setting

## 📚 安装指南
你的下一台电脑何必是电脑？吃灰了几年的 iPad Pro 没实现，被新买的鸿蒙平板实现了。尤其是在如今折叠屏横行的时代，找个星巴克，随时随地展开屏幕，打开折叠键盘就能原地干（装）活（叉）。

本指南主要汇集了我自己使用的语言安装步骤和避坑指南。由于能力有限，未必涵盖所有语言，如果有未涉及到的内容或出错的地方，欢迎指出！

---

## 🛠️ .NET 系列

目前测试下来，.NET 6 可以正常使用，以下是安装步骤：

1. **下载 .NET SDK**  
   打开网页 [https://dotnet.microsoft.com/zh-cn/download/dotnet/6.0](https://dotnet.microsoft.com/zh-cn/download/dotnet/6.0)，找到最新/指定版本的 Linux arm64，以下以目前最新的 6.0.425 为例。

2. **复制下载链接**  
   在 VSCode 终端输入以下命令：  
   ```bash
   wget https://download.visualstudio.microsoft.com/download/pr/ec8e29f5-2fbe-47d8-b0c5-81f11434c00f/ba4bd30be448d649e5ddf1991bf76252/dotnet-sdk-6.0.425-linux-arm64.tar.gz
   ```

3. **安装 wget（如有必要）**  
   如果上述命令报错，请执行以下命令：  
   ```bash
   apt update && apt install wget
   ```
   然后再次执行上述命令。

4. **解压并设置环境变量**  
   执行以下命令：  
   ```bash
   mkdir -p $HOME/.dotnet && tar zxf dotnet-sdk-6.0.425-linux-arm64.tar.gz -C $HOME/.dotnet
   echo 'export DOTNET_ROOT=$HOME/.dotnet
   export PATH=$PATH:$HOME/.dotnet' > ~/.bashrc
   ```

5. **验证安装**  
   重新开一个终端，运行 `dotnet`，如果有输出就说明设置成功。

6. **（坑）检查版本**  
   运行 `dotnet --version`，如果有报错，请继续看下去：  
   - **错误**：Couldn't find a valid ICU package installed on the system  
     **解决**：  
     ```bash
     apt install libicu70
     ```
   - **错误**：执行 `dotnet build` 或 `run` 报 "csc.dll" exited with code 139  
     **解决**：需要继续安装 .NET 3.0：  
     ```bash
     wget https://download.visualstudio.microsoft.com/download/pr/eb4ffaf1-b0a9-466d-8440-0220dca8f806/48df585d8d978c5418fa514da6a2bd9b/dotnet-sdk-3.0.103-linux-arm64.tar.gz
     tar zxf dotnet-sdk-3.0.103-linux-arm64.tar.gz -C $HOME/.dotnet
     ```

---

