# BurpCrypto
[![Releases](https://img.shields.io/github/v/release/bxdsjs/BurpCrypto.svg?include_prereleases&style=square)](https://github.com/bxdsjs/BurpCrypto/releases)
[![Downloads](https://img.shields.io/github/downloads/bxdsjs/BurpCrypto/total?label=Release%20Download)](https://github.com/bxdsjs/BurpCrypto/releases/latest)

Burpcrypto is a collection of burpsuite encryption plug-ins, supporting AES/RSA/DES/ExecJs(execute JS encryption code in burpsuite).

English | [简体中文](./README-zh_CN.md)

# 🔧 本 Fork 的改进

本仓库在 [whwlsfb/BurpCrypto](https://github.com/whwlsfb/BurpCrypto) 基础上，合并了 [PR #53](https://github.com/whwlsfb/BurpCrypto/pull/53)（作者 [tomcruiseqi](https://github.com/tomcruiseqi)）并进行了额外修复，主要变更如下：

### 🚀 API 升级
- 从旧的 `burp-extender-api` 升级到 **Montoya API 2025.6**
- 主类 `BurpExtender` 改为实现 `BurpExtension` 接口
- 所有 PayloadProcessor 迁移至 Montoya API
- 兼容 **Burp Suite 2025.6+**

### 🐛 Bug 修复
- **修复 LevelDB 目录创建失败**：使用系统临时目录（`java.io.tmpdir`）存储 LevelDB 数据，解决 Burp 工作目录无写权限时插件无法加载的问题
- **修复 LevelDB 文件锁冲突**：每次插件加载使用唯一文件夹名，解决 Windows 下多实例/重复加载时的文件锁冲突
- **卸载时自动清理**：插件卸载时自动删除临时 LevelDB 数据文件

### 📦 下载
👉 [GitHub Releases](https://github.com/bxdsjs/BurpCrypto/releases/tag/v0.1.9.1-montoya)

# Build
`$ mvn package`
# Usage
- Download the precompiled jar package from [Releases](https://github.com/whwlsfb/BurpCrypto/releases).
- Add this jar package to your burpsuite's Extensions.
- Switch to BurpCrypto tab, select you need Cipher tab.
- Set key or some value.
- press "Add processor", and give a name for this processor.
- Switch to Intruder->Payloads->Payload Processing.
- press "Add", select "Invoke Burp extension", and select processor you just created.
- press "Start attack", have fun!

## Key Example

- Aes Key(UTF8String): abcdefgabcdefg12
- Aes IV(UTF8String): abcdefgabcdefg12
- Rsa X509 Key: MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCC0hrRIjb3noDWNtbDpANbjt5Iwu2NFeDwU16Ec87ToqeoIm2KI+cOs81JP9aTDk/jkAlU97mN8wZkEMDr5utAZtMVht7GLX33Wx9XjqxUsDfsGkqNL8dXJklWDu9Zh80Ui2Ug+340d5dZtKtd+nv09QZqGjdnSp9PTfFDBY133QIDAQAB
- Rsa Modulus: ca27d90f03753cbbc9958011baf701ac99305b63f68e26ab5617593e01d2fb519127fb87bafbe6e0472ec3a038575fa292adadbc79390a955a61b29431f78f4734773048a45dcf100e23cabf2df11a55aa90cd6b024a44eed1096c3b9e1408d46aae54d7291b82fe4b7867c5eaa45e9cc0ba7f7ae3e5593337c7dcbace2d02ed2fbbff26c6df8a32bb26be80603fcd94c6c8dbd67878d77b37fedcf808e3d8f469aaa7c65d033d547a5c8ea9bdd5c89b836c65852f355a5efd9c7137a186a62b5eb0e052c8be3096d3b51133f8a8c108292a296c99d37bad42bcc3f6c39fa5e583582942b4fc4e7ff4b6779fff5bbaddc65b19c7c57d8cdb39b1a994e08d4a2f50793d8f707d069c380baf0f64bfdce3b35d0b5c5c59348a35a082012aaf4991080abf518b55787969ff24186cb95f7e7218c904cf1dcaeb5bed723e305b83f2e85d6f116d2c7400f9e49d904db8a5a3a0701cdb579fbf3128511acd0f789ece1233ed926d705b3b0dfa34bf33f5ae4bdc611a602aa03aaae13400bc7ad3813ea4474dc62de3d0cb1f5aac277d895a75d38f9b920938fa6b1de35bd6132798c122403c685bdb6e5e24bbd70cfb3e968da0b8affd398e539e7c1e7add09891780bcbd278f3900499ae09cee0dc62e3f92e70001bab6d46261d2801a37f80d84d0e39fce6eaedf106a61b5961960641b9db0e4e23c770e6370ac5d61c6c9eb0f07
- Rsa Exponent: 010001
- DES Key: 12345678
- DESede Key: 123456781234567812345678


## Screenshots

AES Example:

![](screenshot/aes.gif)

ExecJs Example (Here is the modified MD5 algorithm):

![](screenshot/execjs.gif)

Quick Crypto:

![](screenshot/quick_crypto.gif)


# 404Starlink
![png](https://github.com/knownsec/404StarLink-Project/raw/master/logo.png)

BurpCrypto has joined [404Starlink](https://github.com/knownsec/404StarLink).
