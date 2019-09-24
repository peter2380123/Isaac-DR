# Nvidia Isaac Object Detection and Domain Randomisation
### Training looks like
![training-gif](img/isaac-training.gif)

### Sample DR training process
Terminal 1, at Unreal Engine directory:
```
./Engine/Binaries/Linux/UE4Editor IsaacSimProject CarterWarehouse_P -vulkan --isaac_sim_config_json="/home/peter/Desktop/EGH400-Projects/2_isaac_sdk/isaac-sdk-2019.2-30e21124/apps/samples/yolo/bridge_config/carter_rgb_detection.json"
```
Click 'Play' in UE4. This should commence a DR sequence. 

To train, in Terminal 2, at Isaac SDK directory:
```
bazel run //apps/samples/yolo:yolo_training 
```

Once the training has started, Isaac Sight becomes available.   

In Terminal 3, go to `~/yolo3_logs` directory (defined in `"log_dir"` in `apps/yolo/keras-yolo3/configs/isaac_object_detection.json`) and do:

```
tensorboard --logdir . 
```

Upon completion, the h5 file will be saved at this (`~/yolo3_logs`) directory.   

*Notes: A training test was conducted with only one epoch - took about 20 minutes to complete. Generated h5 file **NOT** added to this repo as they are exceed file size limit*