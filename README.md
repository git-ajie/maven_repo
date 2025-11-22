# Maven Repository

这是一个用于发布 Android AAR 库到 GitHub Packages 的 Maven 仓库项目。

## 📦 已发布的包

### ffmpeg-kit-https

FFmpeg Kit HTTPS 模块，用于 Android 平台的音视频处理。

- **GroupId:** `io.github.git-ajie`
- **ArtifactId:** `ffmpeg-kit-https`
- **Version:** `6.0-2`
- **依赖坐标:** `io.github.git-ajie:ffmpeg-kit-https:6.0-2`

## 🚀 使用方法

### 1. 配置仓库

在项目的 `build.gradle` 或 `settings.gradle` 中添加 GitHub Packages 仓库：

```gradle
repositories {
    maven {
        url = uri("https://maven.pkg.github.com/git-ajie/maven_repo")
        credentials {
            username = project.findProperty("gpr.user")
            password = project.findProperty("gpr.key")
        }
    }
}
```

### 2. 添加依赖

在模块的 `build.gradle` 中添加依赖：

```gradle
dependencies {
    implementation 'io.github.git-ajie:ffmpeg-kit-https:6.0-2'
}
```

### 3. 配置认证信息

⚠️ **重要：** GitHub Packages 即使是公开仓库也需要认证才能下载依赖。

在用户主目录创建或编辑 `~/.gradle/gradle.properties` 文件：

```properties
gpr.user=你的GitHub用户名
gpr.key=你的GitHub个人访问令牌
```

#### 创建 GitHub 个人访问令牌

1. 访问 [GitHub Personal Access Tokens](https://github.com/settings/tokens)
2. 点击 "Generate new token (classic)"
3. 勾选权限：
   - ✅ `read:packages` - 下载包（必需）
4. 生成并复制令牌到 `gradle.properties`

## 📚 发布新版本

### 添加新的库

1. 将 AAR 文件放入项目根目录
2. 编辑 `artifacts.gradle`，添加新的配置：

```gradle
ext.artifactsToPublish = [
    [
        artifactId: 'ffmpeg-kit-https',
        version: '6.0-2',
        fileName: 'ffmpeg-kit-https-6.0-2.aar',
        groupId: 'io.github.git-ajie'
    ],
    // 添加新的库
    [
        artifactId: 'your-library',
        version: '1.0.0',
        fileName: 'your-library-1.0.0.aar',
        groupId: 'io.github.git-ajie'
    ]
]
```

3. 发布到 GitHub Packages：

```bash
./gradlew publish
```

## 🔧 项目结构

```
maven_repo/
├── build.gradle           # 主构建配置
├── artifacts.gradle       # 发布配置
├── settings.gradle        # 项目设置
├── *.aar                 # AAR 文件
└── gradle/               # Gradle Wrapper
```

## ⚙️ 技术栈

- **Gradle:** 构建工具
- **maven-publish 插件:** 用于发布到 Maven 仓库
- **GitHub Packages:** 托管平台

## 📝 注意事项

- GitHub Packages 所有下载都需要认证（即使是公开包）
- groupId 必须符合 GitHub Packages 规范（使用 `io.github.用户名` 格式）
- 个人访问令牌不要提交到 Git 仓库

## 🔗 相关链接

- [GitHub Packages 文档](https://docs.github.com/en/packages)
- [Gradle Maven Publish 插件](https://docs.gradle.org/current/userguide/publishing_maven.html)
- [查看已发布的包](https://github.com/git-ajie/maven_repo/packages)

## 📄 许可证

请查看各个库的原始许可证信息。