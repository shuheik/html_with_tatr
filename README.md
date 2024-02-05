# html_with_tatr

### Setup
table-transformerとpaddleOCRのインストール
```
git clone https://github.com/microsoft/table-transformer.git
cd table-transformer
conda env create -f environment.yml
conda activate tables-detr
pip install paddlepaddle-gpu -i https://pypi.tuna.tsinghua.edu.cn/simple
pip install paddleocr
```
https://github.com/microsoft/table-transformer からモデルをダウンロード(保存先は一例)
```
mkdir model
wget -P model https://huggingface.co/bsmock/TATR-v1.1-Pub/resolve/main/TATR-v1.1-Pub-msft.pth
```

table-transformer/src内にocr_and_infer.pyを置いて実行
```
cd src
python ocr_and_infer.py --structure_config_path structure_config.json --structure_model_path /path/to/TATR-v1.1-Pub-msft.pth --structure_device cuda --image_dir /path/to/image_dir --out_dir /path/to/output_dir
```

### Evaluation
<table>
  <thead>
    <tr style="text-align: right;">
      <th>Model</th>
      <th>Text</th>
      <th>Test Data</th>
      <th>TEDS</th>
      <th>TEDS-struct</th>
    </tr>
  </thead>
  <tbody>
    <tr style="text-align: right;">
      <td>TATR-v1.1-Pub</td>
      <td>PaddleOCR</td>
      <td>PubTables-1M/val</td>
      <td>0.9019</td>
      <td>0.9767</td>
    </tr>
    <tr style="text-align: right;">
      <td>PPStructureV2</td>
      <td>PaddleOCR</td>
      <td>PubTables-1M/val</td>
      <td>0.7234</td>
      <td>0.8073</td>
    </tr>
  </tbody>
</table>
