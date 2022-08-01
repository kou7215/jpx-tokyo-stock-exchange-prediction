# jpx-tokyo-stock-exchange-prediction (**Disqualified**)
kaggle/jpx-tokyo-stock-exchange-prediction solution using Bidirectional LSTM.<br>
Many participants used LightGBM, however I used LSTM since I couldn't implement to make preprocess speed up.<br>

## Public LB score : 0.58? (half-remembered)<br>
However, This code has running error in test phase after submit so being **disqualified**.

## Points
- Features: basic technical indices and floor difference.<br>
  I used following technical indices.<br>
  - Moving Average (5days, 25days, 75days)
  - RSI
  - Bollinger band
  - MACD & Signal

- Preprocess : StandardScalar after RobustScalar each SecuritiesCode.<br>
  If we apply normalization to whole dataset, scales of several stocks are too tiny or large. <br>
  
- Inference : Storing old data and I used it for create features which use moving average.<br>
  In addition to this, I called independent normalization instances to transform every stock.
  
## Test time error
The reasons of test time errors are the following two.
- Hard cording the number of stocks(2000); I should have inplemented so that it can resize frexible depending on the number of stocks (more / less 2000).<br>
- Shouldn't have used SecuritiesCode as features; We have possibilities of stock listing and bankruptcy
