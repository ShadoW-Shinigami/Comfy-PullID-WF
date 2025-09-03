# Comfy-PullID-WF
PullID Workflow for consistent character dataset creation that can then be used to train loras to get a consistent character

#Instructions

### Custom Nodes Used

Reactor - https://github.com/Gourieff/ComfyUI-ReActor

Patches_II - https://github.com/lldacing/ComfyUI_Patches_ll (Speeds up the workflow by 3X)

PulID_Flux_II - https://github.com/lldacing/ComfyUI_PuLID_Flux_ll (Better PulID with speed optimisations)

Use Everywhere Nodes - https://github.com/chrisgoringe/cg-use-everywhere

KJNodes - https://github.com/kijai/ComfyUI-KJNodes (GET and SET nodes)

Comfyroll Studio - https://github.com/Suzie1/ComfyUI_Comfyroll_CustomNodes (Prompt List)

Negi Tools - https://github.com/natto-maki/ComfyUI-NegiTools (GPT Calls - Have to setup with key)

Impact Pack - https://github.com/ltdrdata/ComfyUI-Impact-Pack

Impact Subpack - https://github.com/ltdrdata/ComfyUI-Impact-Subpack (Face Detailer)

### Models Used

Flux Dev - https://huggingface.co/black-forest-labs/FLUX.1-dev

PulID-flux-0.9.1 - https://huggingface.co/guozinan/PuLID

Upscaler Controlnet - https://huggingface.co/jasperai/Flux.1-dev-Controlnet-Upscaler

Emotion Lora - https://civitai.com/models/914282/expression-helper-20

### Usage

- Upload an Image to the Load Image node.
- Get results from Final Output.
- Recommended to run every prompt once for 11 images. And in case some image gets discarded by the user, then run the discarded prompt 3 more times and get the user to select one of the regenerated images. (There have been cases where crying image does not work out as intended or cases where there are illustration styled images.)
- Save the 11 images as 1.png, 2.png …….. 11.png
- Use the following caption sets. Jane for women and John for men
    
    [Jane.zip](Jane.zip)
    
    [John.zip](John.zip)
    
- Zip the set of Captions and Images.
- Use the FAL-Flux-Fast-Trainer here with these settings:
    - Upload the zip file.
    - Trigger Word - Either John or Jane depending on the gender.
    - Create Masks - Enabled
    - Steps - 1000
    - Is Input Format Already Preprocessed - Enabled
- Trained lora to be used in platform with these settings
    - Trigger either John or Jane depending on gender.
    - Add man/woman to the metadata depending on gender.
        - Use boy child or girl child if the ages are low

### Current Limitations

- Unable to create 2D characters
- Expressions are slightly worse than the Flux base limitations
- There is a weird problem with PulID for flux where it ruins the quality of the images randomly after a couple of runs. Have to run a refiner pass to combat this issue, but it can lead to overly sharp images. Have not seen the overly sharp images cause any issues, post training but this is worth keeping a note of atleast.
