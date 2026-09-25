# ViaBackwards

> ## 关于本仓库（非官方补丁构建）
>
> 本仓库基于 [ViaVersion/ViaBackwards](https://github.com/ViaVersion/ViaBackwards) 上游 master（内部版本 5.12.1-SNAPSHOT），
> 仅包含一个针对 26.3 的修复，构建产物为 `ViaBackwards-5.12.1-recipefix.jar`。
>
> **修复内容**：ViaVersion + ViaBackwards 下，低于 26.3 的客户端进入 26.3 服务器后，配方书里显示的材料/配方内容错乱。
> 原因是 26.3 起 `Ingredient` 的材料显示统一改用 tag 显示（payload 为 `HolderSet`），而 26.2 的 tag 显示只接受一个命名 tag；
> 原实现在遇到「直接物品列表」时写死占位 tag `planks`，于是旧客户端把材料解析成木板。现已按 26.2 语义降级为 `item` / `composite` 显示。
>
> 涉及文件：`common/src/main/java/com/viaversion/viabackwards/protocol/v26_3to26_2/Protocol26_3To26_2.java`
>
> **安装**：与官方版本一致，需同时安装 ViaVersion，然后用本构建替换 `plugins/` 中的 `ViaBackwards-*.jar`。
> 使用 GitHub Actions 构建（`.github/workflows/release.yml`，推送 `v*` 标签自动发版并上传 jar）。
>
> **声明**：本项目为 MikuMC 服务器维护的补丁构建，公开给大众免费使用，MikuMC 服务器与维护者 JunXieX 享有本项目修改部分的著作权；
> 原始代码版权归 ViaVersion 及其贡献者所有，遵循 GPL-3.0（见 `LICENSE`）。请勿将本构建与官方版本混淆。
>
> MikuMC 系列插件交流群：1105054380

[![Latest Release](https://img.shields.io/github/v/release/ViaVersion/ViaBackwards)](https://github.com/ViaVersion/ViaBackwards/releases)
[![Build Status](https://github.com/ViaVersion/ViaBackwards/actions/workflows/build.yml/badge.svg?branch=master)](https://github.com/ViaVersion/ViaBackwards/actions)
[![Discord](https://img.shields.io/badge/chat-on%20discord-blue.svg)](https://viaversion.com/discord)

**Allows the connection of older clients to newer server versions for Minecraft servers.**

Requires [ViaVersion](https://hangar.papermc.io/ViaVersion/ViaVersion) to be installed.

Supported Versions
-
As a plugin, ViaBackwards runs on servers on releases 1.10-latest. You can also use ViaBackwards in ViaFabric or ViaFabricPlus.
- in **ViaFabric**, put ViaBackwards into the `mods` folder
- in **ViaFabricPlus**, put ViaBackwards into the `config/viafabriclus/jars` folder

See [HERE](https://viaversion.com) for an overview of the different Via* projects.

Snapshot support
--------
**ViaBackwards will only be released a few days *after* a Minecraft update** unless the protocol changes of the update were trivial. If you want early-access, usually days or even weeks before the final release, you can subscribe to either:
- [GitHub Sponsors](https://github.com/sponsors/kennytv/sponsorships?sponsor=kennytv&tier_id=385613&preview=false) (preferred option. Use the `/verify` command on this Discord after), or alternatively
- [Patreon](https://www.patreon.com/kennytv/membership) (see the highest tier and make sure to link Patreon to your Discord account under Settings->Connections)
  This also includes access to a private repository with the code, which will be pushed to the public repository after the given delay on a Minecraft update.

Releases/Dev Builds
-
You can find releases in the following places:

- **Hangar (for our plugins)**: https://hangar.papermc.io/ViaVersion/ViaBackwards
- **Modrinth (for our mods)**: https://modrinth.com/mod/viabackwards
- **GitHub**: https://github.com/ViaVersion/ViaBackwards/releases

Dev builds for **all** of our projects are on our Jenkins server:

- **Jenkins**: https://ci.viaversion.com/view/ViaBackwards/

Known issues
-

* 1.17+ min_y and height world values that are not 0/256 **are not supported**. Clients older than
  1.17 will not be able to see or interact with blocks below y=0 and above y=255
* <1.17 clients on 1.17+ servers might experience inventory desyncs on certain inventory click actions
* Sound mappings are incomplete ([see here](https://github.com/ViaVersion/ViaBackwards/issues/326))
* <1.19.4 clients on 1.20+ servers won't be able to use the smithing table. This can be fixed by
  installing [AxSmithing](https://github.com/ViaVersionAddons/AxSmithing)

Other Links
-
**Maven:** https://repo.viaversion.com

**List of contributors:** https://github.com/ViaVersion/ViaBackwards/graphs/contributors

Building
-
After cloning this repository, build the project with Gradle by running `./gradlew build` and take the created jar out
of the `build/libs` directory.

You need JDK 17 or newer to build ViaBackwards.

License
-
This project is licensed under the [GNU General Public License Version 3](LICENSE).

Special Thanks
-
![https://www.yourkit.com/](https://www.yourkit.com/images/yklogo.png)

[YourKit](https://www.yourkit.com/) supports open source projects with innovative and intelligent tools
for monitoring and profiling Java and .NET applications.
YourKit is the creator of [YourKit Java Profiler](https://www.yourkit.com/java/profiler/),
[YourKit .NET Profiler](https://www.yourkit.com/.net/profiler/),
and [YourKit YouMonitor](https://www.yourkit.com/youmonitor/).
