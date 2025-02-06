# 2 Pass Txt2Img (高解析度修復) 範例

以下範例演示如何實現「Hires Fix」功能。

您可以在 [ComfyUI](https://github.com/comfyanonymous/ComfyUI) 中載入這些圖片以獲取完整工作流程。

Hires fix 的原理是先以較低解析度生成圖片，進行放大後再透過 img2img 處理。請注意在 ComfyUI 中 txt2img 和 img2img 是相同的節點，txt2img 是通過向取樣器節點傳送空圖片並使用最大降噪值實現的。

以下是 ComfyUI 中使用基礎潛在空間放大實現的簡單工作流程：

![範例](hiresfix_latent_workflow.png)

## 非潛在空間放大

此範例展示如何將 [esrgan 放大模型](../upscale_models) 用於放大步驟。由於 ESRGAN 在像素空間運作，圖片必須先轉換至像素空間進行放大，完成後再轉回潛在空間。

![範例](hiresfix_esrgan_workflow.png)

## 更多範例

此為更複雜的兩階段工作流程範例：首先生成使用 WD1.5 beta 3 illusion 模型生成的圖片，進行潛在空間放大後，再使用 cardosAnime_v10 模型進行第二階段處理：

![範例](latent_upscale_different_prompt_model.png)
