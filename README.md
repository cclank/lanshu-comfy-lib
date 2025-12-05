# Lansu Z-Image GGUF Workflow Template

这是一个用于 ComfyUI 的工作流模板，专门支持 GGUF 格式的模型加载，可以快速生成高质量图像。

## 文件说明

- `lansu-z-image-gguf.json`: ComfyUI 工作流模板文件，已配置好支持 GGUF 格式模型加载

## 用途

此工作流模板基于 Z-Image Turbo 模型，支持使用 GGUF 格式的 UNET 模型进行图像生成。相比传统的模型格式，GGUF 格式具有以下优势：

- 更小的文件体积
- 更快的加载速度
- 更低的内存占用
- 保持良好的生成质量

## 使用方法

1. 复制 `lansu-z-image-gguf.json` 文件内容
2. 在 ComfyUI 页面中，直接粘贴到空白工作流区域即可

## 必要准备

为了正确运行此工作流，你需要安装并配置 ComfyUI 的 GGUF 插件：

请参考此推文教程完成插件安装和配置：
[Twitter 教程链接](https://x.com/LufzzLiz/status/1996867648123294167?s=20)

### 模型下载

工作流需要以下模型文件，请将其放置在正确的目录中：

```
📂 ComfyUI/
├── 📂 models/
│   ├── 📂 text_encoders/
│   │      └── qwen_3_4b.safetensors
│   ├── 📂 diffusion_models/
│   │      └── z_image_turbo_q4_k_m.gguf (GGUF格式模型)
│   └── 📂 vae/
│          └── ae.safetensors
```

模型下载链接：
- [qwen_3_4b.safetensors](https://huggingface.co/Comfy-Org/z_image_turbo/resolve/main/split_files/text_encoders/qwen_3_4b.safetensors)
- [z_image_turbo_q4_k_m.gguf](https://huggingface.co/Comfy-Org/z_image_turbo/resolve/main/split_files/diffusion_models/z_image_turbo_q4_k_m.gguf)
- [ae.safetensors](https://huggingface.co/Comfy-Org/z_image_turbo/resolve/main/split_files/vae/ae.safetensors)

## 工作流特点

1. 使用 UnetLoaderGGUF 节点加载 GGUF 格式的 UNET 模型
2. 配置了完整的文本编码器、VAE 和采样器
3. 默认提示词："一个美女"
4. 输出分辨率：1024x1024

## 使用步骤

1. 按照上述链接完成 GGUF 插件安装
2. 下载所需模型文件并放置到对应目录
3. 在 ComfyUI 中导入此工作流模板
4. 修改 CLIP Text Encode 节点中的提示词
5. 设置图像尺寸（默认为 1024x1024）
6. 点击队列提示词开始生成图像

## 注意事项

- 确保已正确安装 ComfyUI GGUF 插件
- 确保模型文件路径正确
- 生成图像时需要足够的系统资源

## 声明

本项目仅供学术研究和技术探讨使用，旨在探索GGUF格式模型在ComfyUI中的应用。使用者应遵守以下规定：

1. **学术用途**: 本项目仅限于学术研究、教育学习和技术交流目的
2. **禁止商业用途**: 严禁将本项目或其衍生作品用于任何商业活动
3. **知识产权**: 项目中使用的模型版权归原作者所有
4. **责任限制**: 作者不对因使用本项目而产生的任何后果承担责任

请在使用前充分理解并遵守上述声明。

## 许可证

本项目采用学术研究许可证 (Academic Research License)，详见 [LICENSE](LICENSE) 文件。

主要条款包括：
- 仅限学术研究和技术探讨使用
- 禁止商业用途
- 需要适当的署名
- 衍生作品需采用相同许可条款

如需商业使用，请联系版权所有者获得明确许可。