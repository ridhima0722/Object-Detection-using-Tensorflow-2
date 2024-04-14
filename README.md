INSTALLATION AND SETUP
Step 1. Clone the tensorflow repository : git clone https://github.com/tensorflow/models.git

Step 2.Protobuf download: https://github.com/protocolbuffers/protobuf/releases 

add the protoc file at the same location where python is present .

OBJECT DETECTION ON CUSTOM DATASET

Directory -models\research\object_detection


Step 1.Prepared Images dataset using LabelImg tool : Upload images in - models/research/object_detection/images

Step 2.Converted xml to csv  using script- python xml_to_csv.py

Step 3.Generated Tfrecords using Script - python generate_tfrecord.py --csv_input=images/test_labels.csv --image_dir=images/test --output_path=test.record

python generate_tfrecord.py --csv_input=images/train_labels.csv --image_dir=images/train --output_path=train.record 

step 4.Downloaded Base model using Script- python model_downloader.py

step 5.Edited config file 

step 6.Started trainig using the Script:python model_main_tf2.py --pipeline_config_path==ssd_efficientdet_d0_512x512_coco17_tpu-8.config  --model_dir==training --alsologtostderr

step 7.Exported inference graph using script:python exporter_main_v2.py --trained_checkpoint_dir=training  --pipeline_config_path=ssd_efficientdet_d0_512x512_coco17_tpu-8.config --output_directory inference_graph

step 8 .tested the images using script: inference_graph\saved_model -l labelmap.pbtxt -i test_images\lego_test_images


Files Inside: models\research\object_detection

1.generate_tfrecord.py

2.labelmap.pbtxt

3.model_downloader.py

4.ssd_efficientdet_d0_512x512_coco17_tpu-8.config

5.xml_to_csv.py

Files Inside :models\research

1.setup.py

2.use_protobuf.py






