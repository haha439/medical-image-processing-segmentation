# Don't git clone the original mednext and nnUNet, because there are something wrong when training 2D images

# To run the code
pip install -r requirements.txt

# set the environment variable
export nnUNet_raw_data_base="/MIP/mednext/nnUNet_raw_data_base"
export nnUNet_preprocessed="/MIP/mednext/nnUNet_preprocessed"
export RESULTS_FOLDER="/MIP/mednext/nnUNet_trained_models"
# preprocessing
cd mednext
## set dataset image to binary image and run dataset.py. I put it in  nnUNet_raw_data_base/nnUNet_raw_data/
mednextv1_plan_and_preprocess -t 1 -p13d None -p12d ExperimentPlanner2D_v21_customTargetSpacing_1x1x1

# training
mednextv1_train 2d nnUNetTrainerV2_MedNeXt_S_kernel3 Task001_HyperKvasir all -p nnUNetPlansv2.1_trgSp_1x1x1