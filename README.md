# High-Dimensional-ETL-Pipeline
Scalable ETL pipeline for high-dimensional datasets featuring streaming statistics, fault-tolerant checkpointing, schema validation, and optimized Parquet storage.

⚙️ High-Dimensional ETL Pipeline by NIHAR

Scalable ETL (Extract–Transform–Load) pipeline built with Python, Pandas, NumPy, and PyArrow.

This project processes large high-dimensional datasets in chunks to avoid memory overload, computes incremental statistics (mean & variance) for normalization, validates schema consistency, and exports optimized Parquet files with compression.

The pipeline supports fault-tolerant checkpointing, allowing processing to resume safely after interruptions.

🚀 Features
📦 Chunk-Based Processing
Processes data in configurable chunks
Avoids loading full datasets into memory
Designed for high-dimensional tabular data
Suitable for large-scale preprocessing workflows

📊 Incremental Statistics & Normalization
Online mean & variance computation
Streaming-style normalization without full dataset loading
Stable numerical updates across batches
Automatic standard deviation handling

🛡️ Validation & Data Safety
Column count validation
Schema consistency checks
Null value detection
Prevents corrupted or malformed data from entering pipeline

♻️ Fault-Tolerant Checkpointing
Saves progress using:
stats_checkpoint.npz
progress_checkpoint.json
Pipeline can resume after failure or interruption
Prevents reprocessing already completed chunks

🗂️ Optimized Output
Writes normalized data to Parquet format
Uses ZSTD compression for efficient storage
Atomic write strategy (.tmp → final) to avoid partial files
Output split into partitioned chunks

🛠️ Tech Stack
Python
NumPy — numerical computations
Pandas — data processing
PyArrow — Parquet serialization
Standard library modules:
os
time
json

▶️ How to Run the Pipeline
1️⃣ Clone the repository
git clone https://github.com/YOUR_USERNAME/high-dimensional-etl-pipeline.git
cd high-dimensional-etl-pipeline

2️⃣ Create & activate virtual environment (recommended)
python -m venv venv
venv\Scripts\activate     # Windows
# source venv/bin/activate  # Linux / macOS

3️⃣ Install dependencies
pip install -r requirements.txt

4️⃣ Run the ETL pipeline
python main.py
⚙️ Configuration

You can modify pipeline parameters inside run_pipeline():
run_pipeline(
    chunks=5,
    rows=100000,
    cols=50,
    dtype="float32",
    out_dir="normalized_parquet"
)
Parameters
chunks → number of data batches
rows → rows per chunk
cols → number of features
dtype → numerical precision
out_dir → output directory

📂 Project Structure
high-dimensional-etl-pipeline/
├─ main.py                     # ETL pipeline implementation
├─ requirements.txt            # Dependencies
├─ README.md                   # Project documentation
└─ normalized_parquet/         # Output files (generated)
📈 Example Output

After execution:
Normalized Parquet files saved in output directory
Console preview of:
mean values
standard deviation
processed row count

Example:
Processed 500,000 rows with 50 columns
Output directory: normalized_parquet

🧑‍💻 Author
Nihar Kumar Patel
🎓 Computer Science Engineering Student
⚙️ Interested in Data Engineering, Simulation & ML

Feel free to open issues or suggest improvements!

📄 License
This project is licensed under the MIT License — free to use, modify, and share with attribution.
