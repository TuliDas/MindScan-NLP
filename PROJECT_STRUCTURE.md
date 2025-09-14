```
/project-root
│
├─ /data                # for datasets (CSV, sample data)
│   ├─ reddit_data.csv  # sample Reddit data (post IDs removed)
│   └─ hf_data.csv      # Hugging Face dataset (or sample portion)
│
├─ /notebooks           # collab notebooks
│   ├─ 01_huggingFace_dataset_collection.ipynb
│   ├─ 02_reddit_posts_data_fetching.ipynb
│   ├─ 03_sample_dataset.ipynb
│   ├─ 04_eda.ipynb
│   └─ 05_model_training.ipynb
│
├─ /src                 # Python scripts / modules
│   ├─ fetch_reddit.py
│   ├─ preprocessing.py
│   └─ train_models.py
│
├─ /models              # trained model checkpoints
│
├─ /results             # evaluation results, plots, metrics
│
├─ README.md
├─ requirements.txt
└─ .gitignore
```
