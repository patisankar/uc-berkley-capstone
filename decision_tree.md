### visualization

For a Decision Tree, we use a pairplot during EDA to visually explore relationships between numerical features and identify patterns related to fraud.

### extract

```python

from sklearn.tree import export_text

tree_rules = export_text(
    dtree,
    feature_names=list(X.columns)
)

print(tree_rules)
```
This prints the fitted decision tree as readable rules, for example:

### cost_complexity_pruning_path
determine how much a decision tree should be pruned to reduce overfitting.

