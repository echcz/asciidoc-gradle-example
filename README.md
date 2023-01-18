# asciidoc-gradle-example

在 gradle 项目中使用 Asciidoc 文档的示例。

## 使用说明

### 生成 HTML 文档

在项目根目录执行命令：

``` console
$ ./gradlew asciidoctor
```

这将在 `build/docs/asciidoc` 目录生成 `index.html`，使用浏览器打开即可查看文档。

### 生成 PDF 文档

在项目根目录执行命令：

``` console
$ ./gradlew asciidoctorPDF
```

这将在 `build/docs/asciidocPdf` 目录生成 `index.pdf` 文档。

> 注意：请确保 `build.gradle` 中的 `asciidoctorPdf.fontsDir` 配置项指定的目录中存在 `src/docs/asciidoc/themes/cjk-theme.yml` PDF 主题文件配置的字体文件。
更多相关信息请查看 [AsciidoctorPdf 文档](https://docs.asciidoctor.org/pdf-converter/latest/theme/cjk/) 与 [Asciidoctor Gradle Plugin 用户指南](https://asciidoctor.github.io/asciidoctor-gradle-plugin/development-3.x/user-guide/#asciidoctorj-pdf-plugin)。

> `cjk-theme.yml` 主题使用的字体文件可在 [echcz/FontsTTF](https://github.com/echcz/FontsTTF) 下载。

### 发布到 Github Pages

1. 在仓库中创建 gh-pages 分支，关联到远程分支
2. 进入到主分支（main 或 master）
3. 修改 `build.gradle` 文件中的 `gitPublish.repoUri` 配置项值为你自己仓库对应的 Github 地址
4. 执行命令 `./gradlew gitPublishPushAfterUpdate`
5. 将 gh-pages 分支发布到 Github Pages

此后，有内容更新，只需要执行 `./gradlew gitPublishPushAfterUpdate` 即可。

> 注意：发布后，gh-pages 分支里的内容会保持和 `build/docs/asciidoc` 里的一致，对里面所有手动更改的内容都会丢失。所以，不要手动修改 gh-pages 分支里的内容。

## 参与贡献

1. Fork 本仓库
2. 新建 Feat_xxx 分支
3. 提交代码
4. 新建 Pull Request
