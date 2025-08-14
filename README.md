#### 安装 PyTorch

Windows 平台需要额外手动安装 GPU 版本的 PyTorch 依赖包，您可以参考[官方网站](https://pytorch.org/get-started/locally/)和以下命令安装并测试 PyTorch 是否正确安装。

```bash
pip uninstall torch torchvision torchaudio
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126
python -c "import torch; print(torch.cuda.is_available())"
```

如果看到 `True` 则说明安装成功。

若遇到类似 `Can't pickle local object` 的报错，请设置 `dataloader_num_workers: 0`。