## **开源雨林**

开源雨林是由华为技术有限公司和开放原子开源基金会、中国软件行业协会、中国科学院软件研究所、中国信息通信研究院等组织共同发起，围绕开源通识、开源治理和开源使用实践等方向构建一个用于收集、分享开源知识分享社区的经验。

### **编译开源雨林**

开源雨林的内容使用 `mdbook` 进行编写，并通过 开源雨林 发布。

#### **安装 mdbook**

1. 在本地安装 `mdbook` 命令编译预览页面。在 `mdbook` 的官方发布页面 下载对应架构的程序包，并将其解压到本地的目录，并把目录添加到 PATH 环境变量中。
2. 在本地通过安装 `Rust` ，然后通过 `Rust` 安装 `mdbook` 命令。

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
cargo install mdbook
# 或
cargo install --git https://github.com/rust-lang/mdBook.git mdbook
```

#### **编译开源雨林**

下载开源雨林的代码到本地，并解压编译

```bash
wget https://github.com/opensource-rainforest/osr/archive/refs/heads/main.zip
tar -xzf main.zip
cd osr-refs-main
mdbook build
```

在浏览器中打开 http://localhost:3000 访问开源雨林的内容页面。

### **品牌**

![开源雨林 Logo](/src//images/Logo-Horizontal.png)

> 开源雨林网站（以及内容托管平台）上使用和显示的所有商标、标志皆属开源雨林社区所有，但注明属于其他方拥有的商标、标志除外。未经开源雨林社区或其他方书面许可，开源雨林网站（以及内容托管平台）所载的任何内容不应被视作以暗示、不反对或其他形式授予使用前述任何商标、标志的许可或权利。 未经事先书面许可，任何人不得以任何方式使用开源雨林的名称及开源雨林的商标、标记，除非你使用前述名称、商标和标记是出于个人、教育和非商业目的。任何人不得在未获得第三方同意的情况下使用第三方拥有的商标和标志。

### **License**

开源雨林使用 [Creative Commons Attribution-ShareAlike 4.0 International](/LICENSE.md) 协议。