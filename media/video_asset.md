# 视频素材报告 — AI+空天防务产业园（多媒体版）

## 一、资产清单

| 项目 | 值 |
|---|---|
| 本地文件路径 | `media/park_showreel.mp4`（相对多媒体版目录） |
| 绝对路径 | `C:\Users\EDY\Desktop\AI+空天防务产业园\商业计划书HTML\多媒体版\media\park_showreel.mp4` |
| 云端备用 URL | https://aka.doubaocdn.com/s/aIsmXOW8VZ |
| 时长 | 15 秒 |
| 分辨率 | 1280 × 720（720p，16:9） |
| 格式 | MP4（容器 brand `isom`，H.264） |
| 文件大小 | 3,700,302 字节（约 3.5 MB） |
| 来源 | AI 文生视频生成（seedance_2.0_fast），非第三方直链 |
| 内容性质 | 产业园区概念宣传片（未来感低空经济园区航拍） |

## 二、实测可访问性结论

- **本地文件**：已落盘，文件头字节为 `00 00 00 1C 66 74 79 70 69 73 6F 6D`，即标准 `ftypisom` MP4 头，确认为合法可播放 MP4，非空文件/非错误页。可直接用本地 `<source src="media/park_showreel.mp4">`。
- **云端 URL**（https://aka.doubaocdn.com/s/aIsmXOW8VZ）：已通过 `Invoke-WebRequest` 实际下载成功（HTTP 200，二进制视频流），内容即上述 mp4。可作为备用外链。
- **方案 a（公开直链 mp4/webm）结论**：检索到的候选均为付费素材站（光厂 vjshi）、PDF 手册或企业 HTML 介绍页，未找到可稳定返回 200 且为视频内容的免费直链，故放弃 a，采用 b 生成。
- **URL 长期有效性提示**：`aka.doubaocdn.com` 为豆包临时短链，**不保证长期有效**；对外发布的 HTML 请以**本地相对路径 `media/park_showreel.mp4`** 为主源，云端 URL 仅作临时备用，不要把它当作永久 CDN。

## 三、内容与合规口径

- 画面元素：现代化研发楼群航拍、民用工业无人机编队、eVTOL 电动垂直起降飞行器在园区起降平台起降、屋顶球形光电监测设备与小型通信雷达天线（民用低空安防/要地防护/公共安全监管用途）。
- 合规：全片无军事部署、无武器装备、无作战车辆、无军人形象；安防设施统一按"民用低空安防/要地防护/公共安全装备"口径呈现。
- 画面无任何文字、水印、logo 或字幕，可直接嵌入商业计划书。

## 四、嵌入 HTML 建议代码

主源用本地相对路径，云端短链作 `<source>` 备源（若未来本地缺失可兜底），`controls` 原生播放，`preload="metadata"` 减少首屏负担：

```html
<video
  controls
  preload="metadata"
  width="100%"
  style="max-width:1280px;display:block;margin:0 auto;background:#000;"
  poster=""
>
  <source src="media/park_showreel.mp4" type="video/mp4" />
  <!-- 备用外链（临时短链，可能失效）；本地文件存在时浏览器会优先使用上面的本地源 -->
  <source src="https://aka.doubaocdn.com/s/aIsmXOW8VZ" type="video/mp4" />
  您的浏览器不支持 HTML5 视频播放。可访问备用链接观看：
  <a href="https://aka.doubaocdn.com/s/aIsmXOW8VZ">园区概念宣传片（15秒，720p MP4）</a>
</video>
```

说明：
- `poster` 留空即显示视频首帧；如需封面图，可另存一张 16:9 概念图为 `media/video_poster.jpg` 并填回 `poster="media/video_poster.jpg"`（当前未生成，非必需）。
- 若 HTML 与 `media/` 目录同级放置，上述相对路径直接可用；若 HTML 在子目录，调整为相对路径（如 `../media/park_showreel.mp4`）。
- 移动端/大屏均可直接播放 MP4/H.264，无需额外转码。
