# 2 Pass Txt2Img (Hires fix) Examples  
# 二次處理 Txt2Img（高解析度修復）範例  

These are examples demonstrating how you can achieve the "Hires Fix" feature.  
這些範例展示如何實現「高解析度修復」功能。  

You can Load these images in [ComfyUI](https://github.com/comfyanonymous/ComfyUI) to get the full workflow.  
您可將這些圖片載入 [ComfyUI](https://github.com/comfyanonymous/ComfyUI) 以獲取完整工作流程。  

Hires fix is just creating an image at a lower resolution, upscaling it and then sending it through img2img. Note that in ComfyUI txt2img and img2img are the same node. Txt2Img is achieved by passing an empty image to the sampler node with maximum denoise.  
高解析度修復的原理是：先以較低解析度生成圖片，將其放大後再透過 img2img 處理。需注意在 ComfyUI 中，txt2img 和 img2img 使用相同節點。Txt2Img 是透過向採樣器節點傳遞空圖像並使用最大降噪值實現的。  

Here's a simple workflow in ComfyUI to do this with basic latent upscaling:  
以下是在 ComfyUI 中使用基礎潛在空間放大實現此功能的簡單工作流程：  

![範例](hiresfix_latent_workflow.png)  

## Non latent Upscaling  
## 非潛在空間放大  

Here is an example of how the [esrgan upscaler](../upscale_models) can be used for the upscaling step. Since ESRGAN operates in pixel space the image must be converted to pixel space and back to latent space after being upscaled.  
此範例展示如何使用 [ESRGAN 放大模型](../upscale_models) 進行放大步驟。由於 ESRGAN 在像素空間運作，圖像放大後需從潛在空間轉換回像素空間，處理完畢後再轉換回潛在空間。  

![範例](hiresfix_esrgan_workflow.png)  

## More Examples  
## 更多範例  

Here is an example of a more complex 2 pass workflow, This image is first generated with the WD1.5 beta 3 illusion model, latent upscaled and then a second pass is done with cardosAnime_v10:  
此為更複雜的二次處理工作流程範例：首先生成使用 WD1.5 beta 3 幻覺模型的圖像，進行潛在空間放大後，再使用 cardosAnime_v10 模型進行二次處理：  
  
![範例](latent_upscale_different_prompt_model.png)
