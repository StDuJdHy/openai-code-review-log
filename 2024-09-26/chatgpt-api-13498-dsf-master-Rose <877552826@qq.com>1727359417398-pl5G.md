### 代码评审

#### build.sh
- **变更**：将 Docker 构建标签从 `doushifu/ChatGPT-api` 更改为 `doushifu/ChatGPT-data-app`。
- **分析**：这个变更可能意味着项目从构建 API 应用程序转变为构建数据应用程序。需要确认这个变更是否符合项目需求。

#### ChatGPT-data-app/pom.xml
- **变更**：添加了新的依赖项 `cn.bugstack:ChatGLM-sdk-java`。
- **分析**：这个依赖项可能用于集成新的 ChatGLM SDK。需要确认这个 SDK 的作用和它如何与现有代码集成。

#### ChatGPT-data-app/src/main/java/com/dsfzl/ChatGPT/data/config/ChatGLMSDKConfig.java
- **变更**：创建了一个新的配置类 `ChatGLMSDKConfig`，其中包含一个 Bean `openAiSession`。
- **分析**：这个配置类可能用于初始化和配置新的 ChatGLM SDK 会话。需要确认这个类的作用和它如何与现有的 `ChatGPTSDKConfig` 类协同工作。

#### ChatGPT-data-app/src/main/java/com/dsfzl/ChatGPT/data/config/ChatGLMSDKConfigProperties.java
- **变更**：创建了一个新的配置属性类 `ChatGLMSDKConfigProperties`。
- **分析**：这个类可能用于存储 ChatGLM SDK 的配置信息，如 API 主机和 API 密钥。需要确认这些属性如何被使用。

#### ChatGPT-data-app/src/main/java/com/dsfzl/ChatGPT/data/config/ChatGPTSDKConfig.java
- **变更**：注释掉了 `ChatGPTSDKConfig` 类的代码。
- **分析**：这个变更可能意味着 `ChatGPTSDKConfig` 类不再使用，或者其功能被 `ChatGLMSDKConfig` 类取代。需要确认这一点并删除不必要的代码。

#### ChatGPT-data-app/src/main/resources/application-dev.yml
- **变更**：更新了 `server.port` 和 `ChatGPT` 相关的配置。
- **分析**：这个变更可能是因为端口更改或配置更新。需要确认这些变更是否符合项目需求。

#### ChatGPT-data-domain/pom.xml
- **变更**：添加了新的依赖项 `cn.bugstack:ChatGLM-sdk-java`。
- **分析**：与 `ChatGPT-data-app` 中的变更类似，这个依赖项可能用于集成新的 ChatGLM SDK。

#### ChatGPT-data-domain/src/main/java/com/dsfzl/ChatGPT/data/domain/openai/service/AbstractChatService.java
- **变更**：在 `AbstractChatService` 类中替换了 `openAiSession` 的类型为 `cn.bugstack.ChatGLM.session.OpenAiSession`。
- **分析**：这个变更可能意味着项目正在从旧的 SDK 切换到新的 ChatGLM SDK。需要确认这个替换的影响和兼容性。

#### ChatGPT-data-domain/src/main/java/com/dsfzl/ChatGPT/data/domain/openai/service/ChatService.java
- **变更**：在 `ChatService` 类中替换了 `openAiSession` 的类型为 `cn.bugstack.ChatGLM.session.OpenAiSession`，并更新了相关方法。
- **分析**：这个变更与 `AbstractChatService` 类中的变更类似，需要确认其影响和兼容性。

#### ChatGPT-data-trigger/pom.xml
- **变更**：添加了新的依赖项 `cn.bugstack:ChatGLM-sdk-java`。
- **分析**：与前面的变更类似，这个依赖项可能用于集成新的 ChatGLM SDK。

#### ChatGPT-data-trigger/src/main/java/com/dsfzl/ChatGPT/data/trigger/http/ChatGPTAIServiceController.java
- **变更**：在 `completionsStream` 方法中添加了新的参数 `completionsStream1`。
- **分析**：这个变更可能是因为方法签名更新。需要确认这个变更的影响。

#### ChatGPT-data-trigger/src/main/java/com/dsfzl/ChatGPT/data/trigger/http/dto/ChatGPTRequestDTO.java
- **变更**：在 `ChatGPTRequestDTO` 类中没有明显的变更。
- **分析**：需要确认这个类是否仍然满足需求。

#### pom.xml
- **变更**：添加了新的依赖项 `cn.bugstack:ChatGLM-sdk-java`。
- **分析**：与前面的变更类似，这个依赖项可能用于集成新的 ChatGLM SDK。

### 差异代码展示

```diff
diff --git a/build.sh b/build.sh
index 42237eb..9428af3 100644
--- a/build.sh
+++ b/build.sh
@@ -1 +1 @@
-docker build -f ./Docker