### 这是一个虚拟数字人的项目，未来会集成《道诡异仙》中的主角李火旺的大模型作为虚拟数字人，会专门制作一个他疯言疯语的形象
* 基于Qwen3-4B-Instruct的微调模型已经上传到modelscope
  * https://modelscope.cn/models/sungo91/Qwen3-4B-Instruct-lihuowang

#### 安装 PyTorch

Windows 平台需要额外手动安装 GPU 版本的 PyTorch 依赖包，您可以参考[官方网站](https://pytorch.org/get-started/locally/)和以下命令安装并测试 PyTorch 是否正确安装。

```bash
pip uninstall torch torchvision torchaudio
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126
python -c "import torch; print(torch.cuda.is_available())"
```

如果看到 `True` 则说明安装成功。

若遇到类似 `Can't pickle local object` 的报错，请设置 `dataloader_num_workers: 0`。

#### LAM数字人驱动Handler依赖模型
* facebook/wav2vec2-base-960h (https://modelscope.cn/models/AI-ModelScope/wav2vec2-base-960h)
  * 从huggingface下载, 确保lfs已安装，使当前路径位于项目根目录，执行：
  ```
  git clone --depth 1 https://huggingface.co/facebook/wav2vec2-base-960h ./models/wav2vec2-base-960h
  ```
  * 从modelscope下载, 确保lfs已安装，使当前路径位于项目根目录，执行：
  ```
  git clone --depth 1 https://www.modelscope.cn/AI-ModelScope/wav2vec2-base-960h.git ./models/wav2vec2-base-960h
  ```
* LAM_audio2exp (https://huggingface.co/3DAIGC/LAM_audio2exp)
  * 从huggingface下载, 确保lfs已安装，使当前路径位于项目根目录，执行：
  ```
  wget https://huggingface.co/3DAIGC/LAM_audio2exp/resolve/main/LAM_audio2exp_streaming.tar -P ./models/LAM_audio2exp/
  tar -xzvf ./models/LAM_audio2exp/LAM_audio2exp_streaming.tar -C ./models/LAM_audio2exp && rm ./models/LAM_audio2exp/LAM_audio2exp_streaming.tar
  ```
  * 国内用户可以从oss地址下载, 使当前路径位于项目根目录，执行：
  ```
  wget https://virutalbuy-public.oss-cn-hangzhou.aliyuncs.com/share/aigc3d/data/LAM/LAM_audio2exp_streaming.tar -P ./models/LAM_audio2exp/
  tar -xzvf ./models/LAM_audio2exp/LAM_audio2exp_streaming.tar -C ./models/LAM_audio2exp && rm ./models/LAM_audio2exp/LAM_audio2exp_streaming.tar
  ```


#### windows下出现'gbk'编码相关的错误
  ``` 
可以手动设置环境变量，高级系统设置->环境变量->系统变量->新建变量-PYTHONUTF8，值为=1,记得重启电脑生效。
  ```

#### 运行
```bash
python src/demo.py
```

#### 感谢
* https://github.com/HumanAIGC-Engineering/OpenAvatarChat
* https://github.com/HumanAIGC-Engineering/gradio-webrtc
* https://github.com/snakers4/silero-vad
* https://github.com/aigc3d/LAM

