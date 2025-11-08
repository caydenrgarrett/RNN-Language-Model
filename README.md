# RNN Language Model <br>

![image alt](https://apt-web.transforms.svdcdn.com/production/images-people/Shakespeare-William-_-banner.png?w=1000&h=750&auto=compress%2Cformat&fit=crop&dm=1704733878&s=a3131fae3f3d72f5f07731808a270be4)

This repository contains a minimal character-level recurrent neural network (RNN) language model trained on the "Tiny Shakespeare" corpus popularized by Andrej Karpathy. The code was originally authored in Google Colab and kept here both as a Jupyter notebook and as the exported Python script that mirrors the notebook cells.

## Repository structure

- `RNN Language Model/`
  - `RNN_Language_Model.ipynb` – the original Colab notebook. Open this if you want the exact interactive environment the model was built in.
  - `rnn_language_model.py` – the notebook exported to a Python script. The script still contains notebook-style commands (for example `!wget`), so it is best treated as reference code or executed inside an interactive environment that understands shell magics (such as Jupyter).
- `LICENSE` – licensing information for the project.

## Requirements

The notebook/script expects the following software stack:

- Python 3.8+
- [PyTorch](https://pytorch.org/) (tested with version 2.x)
- Jupyter (optional, but recommended for running the notebook)

If you plan to run the code locally, install the dependencies inside a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
pip install torch jupyter
```

## Dataset

Training uses the Tiny Shakespeare dataset downloaded from Karpathy's `char-rnn` repository. The notebook/script automatically fetches the data with:

```python
!wget https://raw.githubusercontent.com/karpathy/char-rnn/master/data/tinyshakespeare/input.txt -O tiny_shakespeare.txt
```

You can also download the file manually and place it in the project directory if you prefer not to use the shell command inside Jupyter.

## Running the model

1. **Launch Jupyter** (recommended):
   ```bash
   jupyter notebook
   ```
   Then open `RNN Language Model/RNN_Language_Model.ipynb` and run the cells sequentially.

2. **Or execute the exported script** inside an environment that supports notebook magics (e.g., `ipython`):
   ```bash
   ipython RNN\ Language\ Model/rnn_language_model.py
   ```

During training, the script samples random contiguous batches of 64 characters and trains for 2,000 steps using an `nn.RNN` layer with a hidden size of 128. Progress is printed every 200 steps. After training, the model generates ~300 characters of text conditioned on the prompt `"KING: "`.

## Customization

- Adjust `block_size`, `batch_size`, and the training loop (`range(2000)`) to change the context length, batch size, or the number of optimization steps.
- Modify the `hidden_size` parameter in `RNNLanguageModel` to increase or decrease the capacity of the network.
- Replace the dataset download URL with your own text corpus to experiment with different domains.

## License

This project is distributed under the terms of the MIT License. See the [LICENSE](LICENSE) file for full details.
