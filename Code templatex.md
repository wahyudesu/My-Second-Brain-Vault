	```python
.style.background_gradient(cmap='Blues')
```

## Correlation matrix

![[Pasted image 20231116014514.png|450]]
```python
def correlation_matrix(dataframe):
    corr = dataframe.corr()
    f, ax = plt.subplots(figsize=(14, 11))
    mask = np.triu(np.ones_like(corr))
    sns.heatmap(corr, annot=True, mask = mask, cmap="Reds")
    return ax
correlation_matrix(x)
```
## Confusion matrix
![[Pasted image 20230924144126.png]]]


![[Pasted image 20231116014314.png|500]]
```python
# confution matrix after normalization
import matplotlib.pyplot as plt
target_names = ["business", "entertainment", "politics", "sport", "tech"]

def plot_confusion_matrix(a, b, column, title,cmap="Blues"):
    cm = confusion_matrix(a, b)
    #Normalise
    #cm = cm.astype('float') / cm.sum(axis=1)[:, np.newaxis]
    fig, ax = plt.subplots(figsize=(7,6))
    plt.title(title, fontsize = 15)
    sns.heatmap(cm, annot=True, fmt='.2f', xticklabels=column, yticklabels=column, cmap=plt.cm.Blues)
    plt.ylabel('True label \n', fontsize=15)
    plt.xlabel('\n Predicted label', fontsize=15)
    plt.show()

plot_confusion_matrix(ytest, model.predict(X_test), column = target_names, title="Confusion matrix \n")
```


```python
# Create a copy of the dataframe
df_encoded = train.copy()

# Assuming these are your categorical variables, including 'outcome'
categorical_vars = ['surgery', 'age', 'temp_of_extremities', 'peripheral_pulse', 
                    'mucous_membrane', 'capillary_refill_time', 'pain', 'peristalsis', 
                    'abdominal_distention', 'nasogastric_tube', 'nasogastric_reflux', 
                    'rectal_exam_feces', 'abdomen', 'abdomo_appearance', 'surgical_lesion', 
                    'cp_data', 'outcome']

# Label encode categorical columns
label_encoders = {}
for column in categorical_vars:
    le = LabelEncoder()
    df_encoded[column] = le.fit_transform(train[column])
    label_encoders[column] = le

def plot_correlation_heatmap(df: pd.core.frame.DataFrame, title_name: str = 'Train correlation') -> None:
    excluded_columns = ['id']
    columns_without_excluded = [col for col in df.columns if col not in excluded_columns]
    corr = df[columns_without_excluded].corr()
    
    fig, axes = plt.subplots(figsize=(14, 10))
    mask = np.zeros_like(corr)
    mask[np.triu_indices_from(mask)] = True
    sns.heatmap(corr, mask=mask, linewidths=.5, cmap='YlOrBr_r', annot=True, annot_kws={"size": 6})
    plt.title(title_name)
    plt.show()

# Plot correlation heatmap for encoded dataframe
plot_correlation_heatmap(df_encoded, 'Encoded Dataset Correlation')
```

```python
def evaluation(y_test, y_pred):
    confusion_mat = conf_mat(y_test, y_pred)
    tn, fp, fn, tp = confusion_mat[0, 0], confusion_mat[0, 1], confusion_mat[1, 0], confusion_mat[1, 1]
    print(pd.Series({
        "Accuracy": (tp + tn) / (tn + fp + fn + tp),
        "Precision": tp / (tp + fp),
        "Recall": tp / (tp + fn),
        "F1-score": (2 * tp) / ((2 * tp) + fn + fp),
        "F2-score": (5 * tp) / ((5 * tp) + (4 * fn) + fp),
        "MCC": ((tp * tn) - (fp * fn)) / np.sqrt((tp + fp) * (tp + fn) * (tn + fp) * (tn + fn))
    }).to_string())
```
