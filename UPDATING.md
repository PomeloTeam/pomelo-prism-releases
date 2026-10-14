# Pomelo Prism 官网版更新发布仓库

## 固定地址

- Pages：https://pomeloteam.github.io/pomelo-prism-releases/
- 更新清单：https://pomeloteam.github.io/pomelo-prism-releases/appcast.xml
- 安装包发布：https://github.com/pomeloteam/pomelo-prism-releases/releases

## 当前状态

这是初始仓库结构，不是已完成的自动更新服务。
appcast.xml 目前没有任何版本条目，也尚未签名，可以先用于建立托管路径。
官网 App 中的签名公钥仍未配置，更新器保持关闭。
启用前必须用 Sparkle generate_appcast 生成并签名正式清单；
不能直接把当前初始清单当作正式更新清单。

## 文件放置

- 本仓库提交：.nojekyll、.gitignore、appcast.xml、更新说明以及 Sparkle 生成的清单/说明签名文件。
- DMG/ZIP 安装包：上传到 GitHub Releases 的 Assets，不提交到 main 分支。
- Sparkle 工具包：不提交到 main 分支。
- Developer ID 证书和任何签名私钥：不上传、不提交。

## 正式发布顺序

1. 在本机生成 Sparkle 更新密钥，仅将公钥放入官网 App。
2. 递增 Build 号，签名、公证并制作带版本号的安装包。
3. 使用 Sparkle generate_appcast 生成清单、更新包签名，并按 App 的签名清单要求生成相应签名。
4. 先上传安装包到对应 GitHub Release，确认文件地址可访问。
5. 确认清单中的下载 URL、版本号、长度和签名与最终安装包一致。
6. 以生成的正式清单替换初始 appcast.xml，连同签名和说明手动提交到 main。
7. 等 Pages 部署完成，用上一版本验证检查、下载安装、数据保留和系统代理清理。

已经发布的同版本安装包不要替换；修改内容时发布新的 Build/版本。
本仓库不包含 Pomelo 源码，也不代替 Mac 官网 App 的签名或公证。
