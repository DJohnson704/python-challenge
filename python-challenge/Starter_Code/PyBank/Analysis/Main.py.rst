.. code:: ipython3

    import pandas as pd

.. code:: ipython3

    path = "Resources/budget_data.csv"
    budget_data = pd.read_csv(path)
    budget_data.head()




.. raw:: html

    <div>
    <style scoped>
        .dataframe tbody tr th:only-of-type {
            vertical-align: middle;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    
        .dataframe thead th {
            text-align: right;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>Date</th>
          <th>Profit/Losses</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>Jan-10</td>
          <td>1088983</td>
        </tr>
        <tr>
          <th>1</th>
          <td>Feb-10</td>
          <td>-354534</td>
        </tr>
        <tr>
          <th>2</th>
          <td>Mar-10</td>
          <td>276622</td>
        </tr>
        <tr>
          <th>3</th>
          <td>Apr-10</td>
          <td>-728133</td>
        </tr>
        <tr>
          <th>4</th>
          <td>May-10</td>
          <td>852993</td>
        </tr>
      </tbody>
    </table>
    </div>



.. code:: ipython3

    total_months = budget_data["Date"].nunique()
    total_months




.. parsed-literal::

    86



.. code:: ipython3

    net_total = budget_data["Profit/Losses"].sum()
    net_total




.. parsed-literal::

    22564198



.. code:: ipython3

    budget_data['Change'] = budget_data['Profit/Losses'].diff()
    budget_data["Change"].head()
    




.. parsed-literal::

    0          NaN
    1   -1443517.0
    2     631156.0
    3   -1004755.0
    4    1581126.0
    Name: Change, dtype: float64



.. code:: ipython3

    average_change = budget_data["Change"].mean()
    average_change




.. parsed-literal::

    -8311.105882352942



.. code:: ipython3

    greatest_increase = budget_data["Change"].max()
    greatest_increase
    




.. parsed-literal::

    1862002.0



.. code:: ipython3

    greatest_increase_date = budget_data.loc[budget_data['Change'] == greatest_increase, 'Date'].values[0]
    greatest_increase_date




.. parsed-literal::

    'Aug-16'



.. code:: ipython3

    greatest_decrease = budget_data['Change'].min()
    greatest_decrease




.. parsed-literal::

    -1825558.0



.. code:: ipython3

    greatest_decrease_date = budget_data.loc[budget_data['Change'] == greatest_decrease, 'Date'].values[0]
    greatest_decrease_date




.. parsed-literal::

    'Feb-14'



.. code:: ipython3

    print("Financial Analysis")
    print("-------------------------------------")
    print(f"Total Months: {total_months}")
    print(f"Total: ${net_total}")
    print(f"Average Change: ${average_change:.2f}")
    print(f"Greatest Increase in Profits: {greatest_increase_date} (${greatest_increase:.0f})")
    print(f"Greatest Decrease in Profits: {greatest_decrease_date} (${greatest_decrease:.0f})")


.. parsed-literal::

    Financial Analysis
    -------------------------------------
    Total Months: 86
    Total: $22564198
    Average Change: $-8311.11
    Greatest Increase in Profits: Aug-16 ($1862002)
    Greatest Decrease in Profits: Feb-14 ($-1825558)
    

.. code:: ipython3

    output = "bank.text"
    with open(path, "w") as file:
        file.write(output)
    output




.. parsed-literal::

    'bank.text'



