

import torch

speaker_embeddings = torch.tensor(embeddings_dataset[7306]["xvector"]).unsqueeze(0)

# 第 4 节：从文本和说话人嵌入生成 mel 频谱图

## 从文本和说话人嵌入生成 mel 频谱图

spectrogram = model.generate_speech(inputs["input_ids"], speaker_embeddings)

# 第 5 节：加载 HiFi-GAN 声码器并将频谱图转换为波形：

from transformers import SpeechT5HifiGan

## 加载 HiFi-GAN 声码器以将 mel 频谱图转换为音频

vocoder = SpeechT5HifiGan.from_pretrained("microsoft/speecht5_hifigan")

speech = model.generate_speech(inputs["input_ids"], speaker_embeddings, vocoder=vocoder)

# 第 6 节：播放生成的音频：

from IPython.display import Audio

## 以 16000 Hz 的采样率播放生成的音频

Audio(speech, rate=16000)

从头开始训练完整的 TTS 模型（例如 Tacotron 2），使用 PyTorch 和 torchaudio 是一个复杂的过程。TTS 训练通常需要大量的计算资源和大型数据集（例如 LJ Speech 数据集）才能产生高质量的结果。以下是一个 TTS 模型的简化训练循环示例，其中包括损失函数和其他必要组件。

我们将概述一个基本的 TTS 训练流程，涉及以下内容：

1. 数据集准备：加载数据集并处理文本和音频。
2. 模型定义：一个简化的 TTS 模型。
3. 损失函数：一个频谱损失，以及可选的停止标记损失。
4. 训练循环：用于训练模型的循环。

## 要求

确保您已安装所需的库：

## 第 1 步：数据集准备（以 LJ Speech 为例）：

要加载数据集，我们使用 torchaudio 处理音频文件，并将输入文本准备为音素或字符序列。

import torch

from torch.utils.data import Dataset, DataLoader

import torchaudio

from torchaudio.datasets import LJSPEECH

import torchaudio.transforms as transforms

class TTSDataset(Dataset):

def __init__(self, root, transform=None):

self.dataset = LJSPEECH(root, download=True)

self.transform = transform

def __len__(self):

return len(self.dataset)

def __getitem__(self, idx):

waveform, sample_rate, transcript, *_ = self.dataset[idx]

# 将文本转换为音素或字符序列（基本示例）

text_sequence = torch.tensor([ord(c) for c in transcript.lower() if c.isalnum()], dtype=torch.long)

# 生成 mel 频谱图

mel_spectrogram = transforms.MelSpectrogram()(waveform)

return text_sequence, mel_spectrogram.squeeze(0)

# 加载数据集

dataset = TTSDataset(root="./data")

dataloader = DataLoader(dataset, batch_size=16, shuffle=True, collate_fn=lambda x: x)

## 第 2 步：定义简化的 TTS 模型：

为了演示目的，我们将定义一个基本的编码器-解码器模型，用于从文本输入生成 mel 频谱图。在实际的 TTS 系统中，这会更复杂（例如，带有注意力机制的 Tacotron 2）。

import torch.nn as nn

class SimpleTTSModel(nn.Module):

def __init__(self, vocab_size, embedding_dim=256, hidden_dim=512, mel_bins=80):

super(SimpleTTSModel, self).__init__()

self.embedding = nn.Embedding(vocab_size, embedding_dim)

self.encoder = nn.LSTM(embedding_dim, hidden_dim, batch_first=True)

self.decoder = nn.LSTM(hidden_dim, hidden_dim, batch_first=True)

self.fc = nn.Linear(hidden_dim, mel_bins)

def forward(self, text_sequence):

embedded = self.embedding(text_sequence)

encoder_output, _ = self.encoder(embedded)

decoder_output, _ = self.decoder(encoder_output)

mel_spectrogram = self.fc(decoder_output)

return mel_spectrogram

## 第 3 步：定义损失函数：

该模型使用频谱损失（例如，均方误差）来比较生成的 mel 频谱图和目标 mel 频谱图。可选地，您可以为更复杂的 TTS 系统添加停止标记损失。

import torch.nn.functional as F

def spectrogram_loss(pred, target):

return F.mse_loss(pred, target)

def stop_token_loss(pred_stop, target_stop):

return F.binary_cross_entropy_with_logits(pred_stop, target_stop)

## 第 4 步：训练循环：

现在，我们将设置训练循环，包括优化器和梯度裁剪。

# 模型参数

vocab_size = 128 # 文本序列中使用的 ASCII 字符

model = SimpleTTSModel(vocab_size).to("cuda" if torch.cuda.is_available() else "cpu")

# 优化器

optimizer = torch.optim.Adam(model.parameters(), lr=1e-4)

# 训练循环

epochs = 10

device = torch.device("cuda" if torch.cuda.is_available() else "cpu")

for epoch in range(epochs):

model.train()

total_loss = 0.0

for text_sequence, target_mel in dataloader:

# 移动到设备

text_sequence = text_sequence.to(device)

target_mel = target_mel.to(device)

# 前向传播

predicted_mel = model(text_sequence)

# 计算损失

loss = spectrogram_loss(predicted_mel, target_mel)

# 反向传播和优化

optimizer.zero_grad()

loss.backward()

torch.nn.utils.clip_grad_norm_(model.parameters(), 1.0) # 梯度裁剪

optimizer.step()

total_loss += loss.item()

# 打印本轮的平均损失

avg_loss = total_loss / len(dataloader)

print(f"Epoch [{epoch+1}/{epochs}], Loss: {avg_loss:.4f}")

## 结论

在本章中，我们介绍了使用 TorchAudio 构建 TTS 模型的全面过程，重点介绍了数据预处理、模型训练和评估等关键组件。我们深入探讨了 TTS 系统的架构，强调了 Tacotron 和 WaveNet 等算法在生成自然语音方面的重要性。本章还提供了关于模型开发挑战的实用见解，包括数据对齐、损失函数选择和超参数调整。通过掌握这些技术，您现在已具备创建可应用于各个领域（从无障碍服务到语音助手）的复杂 TTS 模型的能力。这些知识为推进语音合成和深度学习领域提供了关键基础。

在下一章中，我们将探索语音转文本模型。

加入我们书籍的 Discord 空间

加入书籍的 Discord 工作区，获取最新动态、优惠、全球技术动态、新版本以及与作者的会议：

https://discord.bpbonline.com

![](images/Discord.png)

# 第 7 章

## 使用 TorchAudio 将语音转换为文本

## 简介

在当今的数字时代，将口语转换为书面文本至关重要。自动语音识别（ASR）对于转录采访、协助语音助手以及使内容更具可访问性等任务至关重要。在本章中，我们将探索利用深度学习、音频技术和神经网络将口语转换为书面文本的激动人心的过程。这就像一个神奇的过程，将语音转录为书面文字！我们将深入探讨这项技术的机制、可能面临的挑战及其实际应用。

您将学习如何使用 PyTorch 和 TorchAudio 将语音转换为文本（STT），包括创建频谱图和声音。

## 结构

在本章中，我们将学习以下主题：

• 语音转文本转换简介
• 语音转文本转换的应用
• 文本预处理
• 频谱图生成
• 时域转换和声码器基础
• 带 WaveGlow 的语音转文本流程

## 目标

