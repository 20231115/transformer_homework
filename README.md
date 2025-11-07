# transformer_homework

北京交通大学 — 大模型基础与应用（期中作业）

本仓库包含若干基于 Transformer 的实验笔记本（Jupyter/Colab），用于练习 Transformer 的不同变体与超参数设置，并保存了对应的训练检查点。

## 目录结构

根目录（src）下主要包含多个实验子文件夹，每个文件夹通常含有 notebook、数据和 checkpoint 目录：

- `transformer.ipynb` — 用于编写transformer模型
- `transformer_head8/` — 8 头注意力实验
- `transformer_layer6/` — 6 层 Transformer 实验
- `transformer_lr_dynamic/` — 学习率动态调整实验
- `transformer_lr_static_base/` — 静态学习率基线实验
- `transformer_nopos/` — 取消位置编码的对照实验


每个子目录下通常包含：
- `*.ipynb` — 可交互运行的 Jupyter 笔记本
- `data/` — 训练/验证数据（若已下载则放在该目录）
- `checkpoints/`、`checkpoints1/` — 训练保存的模型权重和中间结果

## 快速开始（Windows - cmd）

1. 克隆仓库（若尚未克隆）：

```cmd
git clone https://github.com/20231115/transformer_homework.git
cd transformer_homework
```

2. 建议使用虚拟环境（venv 或 conda）：

```cmd
python -m venv .venv
.venv\Scripts\activate
```

3. 安装常用依赖（根据需要调整版本、或提供的 requirements.txt 列表基础上安装）,这里提供的requirements.txt是本人环境中所有的python包：

```cmd
pip install --upgrade pip
pip install jupyterlab notebook numpy pandas matplotlib tqdm torch torchvision
```

注意：如果需要使用 GPU，请安装与系统 CUDA 版本匹配的 PyTorch（参考 https://pytorch.org/get-started/locally/ ）。

4. 启动 Jupyter 并打开对应 notebook：

```cmd
jupyter lab
```
解压`src/`下data文件夹下的数据压缩包，然后在浏览器中打开 `src/` 下对应的 notebook（例如 `src/transformer_layer6/transformer_layer6.ipynb`），点击全部运行就可以训练。

## 运行/训练笔记

- 每个 notebook 中通常包含数据准备、模型定义、训练循环与评估单元格。按顺序运行单元格即可。
- 如果 notebooks 提示找不到数据或 checkpoint，请先把数据放入对应子文件夹的 `data/`，或修改笔记本里 `data_path` 的指向。
- 训练时间与显卡、批量大小和模型大小相关。对笔记本中长时间训练的单元格，可先把训练轮数设小用于调试。

## 检查点与恢复

- 检查点位于各实验子目录下的 `checkpoints/` 或 `checkpoints1/`。加载模型时请指向正确的 checkpoint 文件路径。
- 若需要从头开始训练，可删除（或移动）对应的 checkpoint 目录再运行训练单元格。

## 常见问题（快速排查）

- "refusing to merge unrelated histories": 如果在拉取远端时出现此类错误，说明本地与远端历史无共同祖先（可能是两个独立的初始化）。常见解决方式有：
	- 若要合并历史：`git pull <remote> main --allow-unrelated-histories`（会产生合并提交，可能需手动解决冲突）。
	- 若以远端为准覆盖本地：备份后 `git fetch <remote>` 然后 `git reset --hard <remote>/main`（会丢弃本地改动）。
	- 若以本地为准强制推送远端：`git push --force-with-lease <remote> main`（高风险，谨慎使用）。

## 贡献者与联系

- 作业作者/提交者：北京交通大学 20231115（仓库 owner）
- 若要反馈问题或提交改进，请在仓库里打开 Issue 或通过课程渠道联系助教。

## 许可证

本仓库作业材料仅供教学与学习使用，未经允许请勿商业分发。若需明确授权，请在仓库中添加 LICENSE 文件或联系作者说明用途。


