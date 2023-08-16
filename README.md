# Generating Radiology Report Impression with Large Language Model on AWS Jumpstart

Our primary focus is on showcasing the effective strategy of fine-tuning open-source pretrained large language models (LLMs) for radiology report summarization, utilizing AWS services. LLMs have consistently displayed remarkable capabilities in natural language understanding and generation, making them versatile foundation models that can be adapted to various domains and tasks.

In our approach, we fine-tune the Flan-T5 XL model, which has a generous maximum input length of 896 tokens, making it capable of accommodating the findings of a typical Chest X-Ray report. This fine-tuning is conducted for the summarization task using a dataset of 91,544 free-text radiology reports obtained from the MIMIC-CXR dataset.

## Obtaining MIMIC CXR Data for Training

To obtain training data for this task, you'll need to first obtain access to the [MIMIC-CXR v2.0 dataset](https://physionet.org/content/mimic-cxr/2.0.0/). Because we are only using the radiology report text data, you do NOT need to download the entire MIMIC-CXR release. The only file you'll need to download from the MIMIC-CXR website is the compressed report file (mimic-cxr-reports.zip).

After obtaining the compressed report file (mimic-cxr-reports.zip), you can make summarization data with the scripts included in this [MEDIQA REPO](https://github.com/abachaa/MEDIQA2021/tree/main/Task3). The scripts will find report IDs that will be used for training and validation, extract and parse the report text from the zip file, and write the resulting data into json files. To do this, run:

```
python make_mimic_data.py MIMIC_CXR_ZIP mimic_split_train_dev.csv \
    --train_file train.json
    --dev_file dev.json
```   
where MIMIC_CXR_ZIP is the path to the compressed report zip file you should have downloaded. Feel free to replace the json file names to whatever you are comfortable with. Note that at this moment, you will only have training and development IDs. Example IDs for the test portion of the MIMIC dataset will be released in a later phase. After successfully running the script, you should be able to see 91,544 total training examples in your train.json file, and 2,000 total development examples in your dev.json file.

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

