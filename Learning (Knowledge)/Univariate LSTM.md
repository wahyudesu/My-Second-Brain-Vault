#time_series
Univariate LSTM (Long Short-Term Memory) models are used to model univariate time series forecasting problems, which are problems comprised of a single series of observations and a model is required to learn from the series of past observations to predict the next value in the sequence. LSTM (Long Short-Term Memory) is a Recurrent Neural Network (RNN) based architecture that is widely used in natural language processing and time series forecasting. The LSTM model will learn a function that maps a sequence of past observations as input to an output observation. As such, the sequence of observations must be transformed into multiple examples from which the LSTM can learn. To prepare data for the LSTM network in Keras, the data must be split into samples, and each sample is a single time series. There are several variations of the LSTM model for univariate time series forecasting, including Vanilla LSTM, Stacked LSTM, Bidirectional LSTM, CNN LSTM, and ConvLSTM.
Dalam konteks prediksi deret waktu, Univariate LSTM dapat digunakan untuk mempelajari pola dan tren dari data historis dan kemudian memprediksi nilai-nilai masa depan berdasarkan pola yang telah dipelajari

Citations:
[1] https://towardsdatascience.com/lstm-framework-for-univariate-time-series-prediction-d9e7252699e
[2] https://machinelearningmastery.com/how-to-develop-lstm-models-for-time-series-forecasting/
[3] https://machinelearningmastery.com/prepare-univariate-time-series-data-long-short-term-memory-networks/
[4] https://www.kaggle.com/code/ritesh7355/develop-lstm-models-for-time-series-forecasting
[5] https://www.kaggle.com/code/amar09/lstm-for-univariate-ts-forecasting
[6] https://towardsai.net/p/l/univariate-time-series-with-stacked-lstm-bilstm-and-neuralprophet