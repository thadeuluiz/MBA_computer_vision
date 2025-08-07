# Hello, these are the instructions for Training NeRFs, 3DGS and more using nerfstudio!

The instructions here will closely follow the nerfstudio [docs](https://docs.nerf.studio/), so check it out if something comes up!

## Data preparation:
First we need a set of  localized views. We know how to do it using COLMAP, but nerfstudio is also able to leverage COLMAP for us! 

To have our data understood by nerfstudio, we follow the basic processing step described [here](https://docs.nerf.studio/quickstart/custom_dataset.html#using-custom-data),

`ns-process-data {video,images,polycam,record3d} --data {DATA_PATH} --output-dir {PROCESSED_DATA_DIR}`

With the Horse set, we chose `images`, and point DATA_PATH to the directory containing the individual frames. If you have a video, you may choose `video` and nerfstudio will automatically extract frames and localize them as well!

There are many options to process data, remember to check out the available options using
`ns-process-data {video,images,polycam,record3d} --help`.

## Training models:
Suppose we save the processed data to the directory `nerfstudio_processed`. Then we may train our nerfs and 3DGS with the commands:

`ns-train nerfacto --data nerfstudio_processed`
`ns-train splatfacto --data nerfstudio_processed`

running these commands will open a local server which you can use to check and visualize training!
If you want to see the available options for each model, 
`ns-train {MODEL_NAME} --help`.

There are many more models available with nerfstudio, which you can check [here](https://docs.nerf.studio/nerfology/methods/index.html).

# Have Fun!
