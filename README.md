# PatchAttackTool
Welcome to our repo for the code for attacks against autonomous driving vision tasks. This code was used to craft the adversarial patches used in our paper "[CARLA-GeAR: a Dataset Generator for a Systematic Evaluation of Adversarial Robustness of Vision Models](https://carlagear.retis.santannapisa.it/)". 

This code constitutes a generalization of our repository https://github.com/retis-ai/SemSegAdvPatch to extend [scene-specific attacks](https://openaccess.thecvf.com/content/WACV2022/html/Nesti_Evaluating_the_Robustness_of_Semantic_Segmentation_for_Autonomous_Driving_Against_WACV_2022_paper.html) to tasks other than **semantic segmentation**, namely **2d object detection**, **monocular depth estimation** and **stereo 3d object detection**.

![image](https://user-images.githubusercontent.com/92364988/173370023-ade7e6cf-dec2-4c75-9a1f-f4ca4405c9fe.png)

Please visit https://carlagear.retis.santannapisa.it/#research for a list of our papers concerning real-world adversarial attacks.

### Installation
We tested the code with Python 3.6.9. It is strongly suggested to use a virtual environment.
Install PyTorch 1.10.1 with CUDA 11.1 support (https://pytorch.org/get-started/previous-versions/ - any CUDA version should work).

Then, install the requirements: `pip install -r requirements.txt`

You should be all set!
If you want to use the same models we used, checkout the Datasets and models section.

### Tasks
To keep the structure general, each task has its own Task Interface object that handles the task-specific optimization and evaluation steps. 
Also, each attack is task-specific and defined in its own class. Models, losses, metrics, and utilities are in the task-specific libraries  `ptsemseg`, `ptod`, `ptdepth`, and `pt3dod`.

This generalization helps maintain the same structure for each task, as well as the possibility to extend the optimization to any user-defined attack of model.

### Datasets and models
This repo is intended to work with CARLA-generated datasets as the ones that you can find [here](https://carlagear.retis.santannapisa.it/#datasets).
This is because the scene-specific attack requires exact camera-to-billboard roto-translation information for accurate patch placing.

The models used for the generation of the patches included in these datasets are in the following table:
| Network  | Link to repo |
| ------------- | ------------- |
| DDRNet23Slim  | Content Cell  |
| BiseNetX39  | Content Cell  |
| Faster R-CNN  | Content Cell  |
| RetinaNet  | Content Cell  |
| GLPDepth  | Content Cell  |
| AdaBins  | Content Cell  |
| Stereo R-CNN  | Content Cell  |

### Running the code
To evaluate the performance of a network, it is sufficient to run 
```python eval_script.py --config path/to/config.yml```, while for the optimization you must run ```python optimization_script.py --config path/to/config.yml```.

The `.yml` config file (of which we shared a template for each network used) is the same for optimization and evaluation. In the latter case, the part dedicated to the optimization is ignored (but results are saved anyway --- so double check the experiment folder to make sure you don't overwrite anything important).


### Extending attacks and models
To extend the code to user-defined, it is sufficient



Code is coming soon.
