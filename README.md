# Comfy-PullID-WF
PullID Workflow for consistent character dataset creation that can then be used to train loras to get a consistent character

#Instructions

### Custom Nodes Used

Reactor - httpsgithub.comGourieffComfyUI-ReActor

Patches_II - httpsgithub.comlldacingComfyUI_Patches_ll (Speeds up the workflow by 3X)

PulID_Flux_II - httpsgithub.comlldacingComfyUI_PuLID_Flux_ll (Better PulID with speed optimisations)

Use Everywhere Nodes - httpsgithub.comchrisgoringecg-use-everywhere

KJNodes - httpsgithub.comkijaiComfyUI-KJNodes (GET and SET nodes)

Comfyroll Studio - httpsgithub.comSuzie1ComfyUI_Comfyroll_CustomNodes (Prompt List)

Negi Tools - httpsgithub.comnatto-makiComfyUI-NegiTools (GPT Calls - Have to setup with key)

Impact Pack - httpsgithub.comltdrdataComfyUI-Impact-Pack

Impact Subpack - httpsgithub.comltdrdataComfyUI-Impact-Subpack (Face Detailer)

### Models Used

Flux Dev - httpshuggingface.coblack-forest-labsFLUX.1-dev

PulID-flux-0.9.1 - httpshuggingface.coguozinanPuLID

Upscaler Controlnet - httpshuggingface.cojasperaiFlux.1-dev-Controlnet-Upscaler

Emotion Lora - httpscivitai.commodels914282expression-helper-20

### Usage

- Upload an Image to the Load Image node.
- Get results from Final Output.
- Recommended to run every prompt once for 11 images. And in case some image gets discarded by the user, then run the discarded prompt 3 more times and get the user to select one of the regenerated images. (There have been cases where crying image does not work out as intended or cases where there are illustration styled images.)
- Save the 11 images as 1.png, 2.png …….. 11.png
- Use the following caption sets. Jane for women and John for men
    
    Jane.zip
    
    John.zip
    
- Zip the set of Captions and Images.
- Use the FAL-Flux-Fast-Trainer here with these settings
    - Upload the zip file.
    - Trigger Word - Either John or Jane depending on the gender.
    - Create Masks - Enabled
    - Steps - 1000
    - Is Input Format Already Preprocessed - Enabled
- Trained lora to be used in platform with these settings
    - Trigger either John or Jane depending on gender.
    - Add manwoman to the metadata depending on gender.
        - Use boy child or girl child if the ages are low

### Current Limitations

- Unable to create 2D characters
- Expressions are slightly worse than the Flux base limitations
- There is a weird problem with PulID for flux where it ruins the quality of the images randomly after a couple of runs. Have to run a refiner pass to combat this issue, but it can lead to overly sharp images. Have not seen the overly sharp images cause any issues, post training but this is worth keeping a note of atleast.
