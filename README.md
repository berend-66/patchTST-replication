# patchTST-replication
Reproducing results from 'A Time Series is Worth 64 Words' (Yuqi Nie, et al., 2023) and 'Are Transformers Effective for Time Series Forecasting?' (Ailing Zeng, et al., 2022)

## CLI Example Runs for a Horizon of 96, with Datasets ETTm1, ETTm2, ETTh1:
Single: 
python run_longExp.py \ 
  --is_training 1 \      
  --model_id ETTm2_336_96 \                       
  --model NLinear \                                                
  --data ETTm2 \                                                      
  --root_path ./dataset/ETT/ \                                              
  --data_path ETTm2.csv \  
  --features M \
  --seq_len 336 \
  --label_len 168 \
  --pred_len 96 \
  --enc_in 7 --dec_in 7 --c_out 7 \
  --batch_size 32 \
  --learning_rate 0.0005 \
  --num_workers 0  \
--itr 3

Multiple:
for d in ETTm1 ETTh1; do
  python run_longExp.py \
    --is_training 1 --model NLinear --features M \
    --model_id ${d}_336_96 --data ${d} --root_path ./dataset/ETT/ \
    --data_path ${d}.csv --seq_len 336 --label_len 168 --pred_len 96 \
    --enc_in 7 --dec_in 7 --c_out 7 --batch_size 32 --learning_rate 0.0005 \
    --num_workers 0 --itr 3

## Recommended to Create a Virtual Environment: 
e.g.: 
  conda create -n ltsf_linear python=3.8 -y
  conda activate ltsf_linear
  pip install -r LTSF-Linear/requirements.txt
and then:
  cd ltfs-linear
