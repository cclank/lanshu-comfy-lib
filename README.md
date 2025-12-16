# Lanshu ComfyUI Library

这是一个专为 ComfyUI 设计的模型加载库，包含工作流模板和 Colab 部署脚本，帮助用户快速体验高效图像生成模型的优势。

## 新增功能支持

### Z-Image-Turbo-Fun-Controlnet 支持

我们现在支持阿里巴巴最新发布的 Z-Image-Turbo-Fun-Controlnet 模型，该模型支持多种控制条件输入，为图像生成提供更多创意可能性。

#### 模型安装步骤：

1. 在 ComfyUI 根目录下创建 `model_patches` 文件夹（如不存在）
2. 下载模型文件：
   ```bash
   wget https://huggingface.co/alibaba-pai/Z-Image-Turbo-Fun-Controlnet-Union-2.0/resolve/main/Z-Image-Turbo-Fun-Controlnet-Union-2.0.safetensors?download=true -O ComfyUI/model_patches/Z-Image-Turbo-Fun-Controlnet-Union-2.0.safetensors
   ```
3. 重启 ComfyUI 服务使模型生效

#### 推荐参数配置：

当使用 QwenImageDiffsynthControlnet 节点时，推荐将 strength 参数设置为 `0.85` 以获得最佳效果。

#### 功能特点：

- 支持多种控制条件输入（如边缘检测、深度图、姿态估计等）
- 与现有 Z-Image Turbo 工作流无缝集成
- 提供更精确的图像控制能力

## 库文件说明

- `lansu-z-image-gguf.json`: ComfyUI 工作流模板文件，已配置好支持 GGUF 格式模型加载
- `zimage-controlnet.json`: ComfyUI ControlNet 工作流模板文件，支持 Z-Image-Turbo-Fun-Controlnet 模型
- `lansu_colab.ipynb`: Google Colab 笔记本文件，可用于在云端快速部署和运行 ComfyUI 及此工作流模板

## 用途

此工作流模板基于 Z-Image Turbo 模型，支持使用 GGUF 格式的 UNET 模型进行图像生成。相比传统的模型格式，GGUF 格式具有以下优势：

- 更小的文件体积
- 更快的加载速度
- 更低的内存占用
- 保持良好的生成质量

### Z-Image-Turbo-Fun-Controlnet 特性

新增的 `zimage-controlnet.json` 工作流支持阿里巴巴最新发布的 Z-Image-Turbo-Fun-Controlnet 模型，该模型具有以下特性：

- 支持多种控制条件输入（如边缘检测、深度图、姿态估计等）
- 与现有 Z-Image Turbo 工作流无缝集成
- 提供更精确的图像控制能力
- 使用 QwenImageDiffsynthControlnet 节点，推荐 strength 参数设置为 `0.85`

## 使用方法

### GGUF 工作流使用方法

1. 复制 `lansu-z-image-gguf.json` 文件内容
2. 在 ComfyUI 页面中，直接粘贴到空白工作流区域即可

### ControlNet 工作流使用方法

1. 复制 `zimage-controlnet.json` 文件内容
2. 在 ComfyUI 页面中，直接粘贴到空白工作流区域即可
3. 确保已安装 Z-Image-Turbo-Fun-Controlnet 模型（见下方模型安装说明）
4. 加载输入图像并调整参数设置

#### ControlNet 示例效果

使用 ControlNet 工作流，您可以基于输入的控制图像生成符合指定条件的图像。例如，您可以使用边缘检测图作为控制条件，生成保持原图轮廓但风格不同的新图像。

本仓库包含一个示例图片文件，展示了 ControlNet 的工作效果：

![ControlNet 示例效果图](Pasted%20Graphic%208.tiff)

您可以使用此图片作为输入进行测试，或加载自己的图像进行实验。推荐使用清晰的图像作为输入以获得最佳效果。

**推荐参数设置**:
- QwenImageDiffsynthControlnet 节点的 strength 参数设置为 `0.85`
- 输入图像建议尺寸为 512x512 至 1024x1024 像素

### Colab 使用方法

对于希望在云端快速体验此工作流的用户，我们提供了 Google Colab 笔记本文件 `lansu_colab.ipynb`：

1. 在 Google Colab 中打开 `lansu_colab.ipynb` 文件
2. 按顺序运行各个代码单元格
3. 笔记本会自动完成以下操作：
   - 克隆 ComfyUI 仓库
   - 安装必要的依赖项
   - 下载所需的模型文件
   - 启动 ComfyUI 服务并通过 Cloudflare Tunnel 提供公网访问地址
4. 获取公网访问地址后，即可在浏览器中访问 ComfyUI 并使用此工作流模板

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
│   ├── 📂 vae/
│   │      └── ae.safetensors
│   └── 📂 model_patches/
│          └── Z-Image-Turbo-Fun-Controlnet-Union-2.0.safetensors (ControlNet模型)
```

模型下载链接：
- [qwen_3_4b.safetensors](https://huggingface.co/Comfy-Org/z_image_turbo/resolve/main/split_files/text_encoders/qwen_3_4b.safetensors)
- [z_image_turbo_q4_k_m.gguf](https://huggingface.co/Comfy-Org/z_image_turbo/resolve/main/split_files/diffusion_models/z_image_turbo_q4_k_m.gguf)
- [ae.safetensors](https://huggingface.co/Comfy-Org/z_image_turbo/resolve/main/split_files/vae/ae.safetensors)
- [Z-Image-Turbo-Fun-Controlnet-Union-2.0.safetensors](https://huggingface.co/alibaba-pai/Z-Image-Turbo-Fun-Controlnet-Union-2.0/resolve/main/Z-Image-Turbo-Fun-Controlnet-Union-2.0.safetensors?download=true)

ControlNet 模型安装命令：
```bash
wget https://huggingface.co/alibaba-pai/Z-Image-Turbo-Fun-Controlnet-Union-2.0/resolve/main/Z-Image-Turbo-Fun-Controlnet-Union-2.0.safetensors?download=true -O ComfyUI/model_patches/Z-Image-Turbo-Fun-Controlnet-Union-2.0.safetensors
```

**注意**: 使用 QwenImageDiffsynthControlnet 节点时，推荐将 strength 参数设置为 `0.85` 以获得最佳效果。

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
- 衍生作品需采用相同许可条款

如需商业使用，请联系版权所有者获得明确许可。