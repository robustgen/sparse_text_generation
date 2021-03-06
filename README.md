
# Sparse Text Generation

This is the repository for our paper [Sparse Text Generation](https://arxiv.org/abs/2004.02644).

# Installation
Before running the code, you need to install the dependencies by running the following lines.
```
cd language_modeling
pip3 install .
```

# Fine-tune GPT2 for Language Modeling

### Training
To fine-tune GPT2 for language modelling you just need to run the following command, modifying the parameters as you wish.
```
python3 examples/run_lm_finetuning.py \
        --train_data_file=/path/to/dataset/train \
        --eval_data_file=/path/to/dataset/eval \
        --output_dir=/path/to/output \
        --model_type=gpt2 \
        --model_name_or_path=gpt2-medium \
        --block_size=512 \
        --do_train \
        --evaluate_during_training \
        --loss=entmax \
        --entmax_alpha=1.2 \
        --top_k=0 \
        --top_p=0
```

### Evaluating
To evaluate a model just run:
```
python3 examples/run_lm_finetuning.py \
        --train_data_file=/path/to/dataset/train \
        --eval_data_file=/path/to/dataset/eval \
        --output_dir=/path/to/output \
        --model_type=gpt2 \
        --model_name_or_path=/path/to/checkpoint_to_evaluate \
        --block_size=512 \
        --do_eval \
        --loss=entmax \
        --entmax_alpha=1.2 \
        --top_k=0 \
        --top_p=0
```

# Fine-tune GPT2 for Dialogue Generation

### Training
To fine-tune GPT2 for dialogue generation you just need to run the following command, modifying the parameters as you wish.
```
python3 train.py 
        --dataset_path=/path/to/dataset \
        --model_checkpoint=gpt2-medium \
        --name=name_you_want_to_give_to_model \
        --loss=entmax \
        --entmax_alpha=1.3 \ 
        --top_p=0 \
        --top_k=0
```
### Evaluating
To evaluate a model just run:
```
python3 eval.py 
        --dataset_path=/path/to/dataset\
        --model_type=gpt2-medium \
        --name=name_you_want_to_give_to_model \
        --model_checkpoint=/path/to/checkpoint_to_evaluate \
        --loss=entmax \
        --entmax_alpha=1.3 \ 
        --top_p=0 \
        --top_k=0
```

# Acknowledgment 
A large portion of the code comes from the awesome Huggingface [Transformers](https://github.com/huggingface/transformers) library.

# Citation

    @inproceedings{martins20sparse,
      author    = {Martins, Pedro Henrique and Marinho, Zita and  Martins, Andr{\'e} FT},
      title     = {Sparse Text Generation},
      booktitle = {Proc. EMNLP (to appear)},
      year      = {2020}
    }
