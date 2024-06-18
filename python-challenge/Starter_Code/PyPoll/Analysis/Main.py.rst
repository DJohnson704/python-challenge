.. code:: ipython3

    import pandas as pd

.. code:: ipython3

    path = "Resources/election_data.csv"
    election_data = pd.read_csv(path)
    election_data.head()




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
          <th>Ballot ID</th>
          <th>County</th>
          <th>Candidate</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>0</th>
          <td>1323913</td>
          <td>Jefferson</td>
          <td>Charles Casper Stockham</td>
        </tr>
        <tr>
          <th>1</th>
          <td>1005842</td>
          <td>Jefferson</td>
          <td>Charles Casper Stockham</td>
        </tr>
        <tr>
          <th>2</th>
          <td>1880345</td>
          <td>Jefferson</td>
          <td>Charles Casper Stockham</td>
        </tr>
        <tr>
          <th>3</th>
          <td>1600337</td>
          <td>Jefferson</td>
          <td>Charles Casper Stockham</td>
        </tr>
        <tr>
          <th>4</th>
          <td>1835994</td>
          <td>Jefferson</td>
          <td>Charles Casper Stockham</td>
        </tr>
      </tbody>
    </table>
    </div>



.. code:: ipython3

    #Total number of cast votes
    total_votes = election_data["Ballot ID"].value_counts()
    total = election_data["Ballot ID"].nunique()
    total, total_votes




.. parsed-literal::

    (369711,
     Ballot ID
     1323913    1
     6316093    1
     5375112    1
     7870527    1
     7789364    1
               ..
     7953257    1
     5932025    1
     5029501    1
     5113956    1
     4660518    1
     Name: count, Length: 369711, dtype: int64)




.. code:: ipython3

    #Number of votes for each candidate
    candidates = election_data["Candidate"].unique()
    candidates




.. parsed-literal::

    array(['Charles Casper Stockham', 'Diana DeGette', 'Raymon Anthony Doane'],
          dtype=object)



.. code:: ipython3

    counts = election_data["Candidate"].value_counts()
    counts




.. parsed-literal::

    Candidate
    Diana DeGette              272892
    Charles Casper Stockham     85213
    Raymon Anthony Doane        11606
    Name: count, dtype: int64



.. code:: ipython3

    percent = (counts/total)*100
    percent = round(percent, 3)
    percent




.. parsed-literal::

    Candidate
    Diana DeGette              73.812
    Charles Casper Stockham    23.049
    Raymon Anthony Doane        3.139
    Name: count, dtype: float64



.. code:: ipython3

    winner = counts.loc[counts == counts.max()].index[0]
    winner




.. parsed-literal::

    'Diana DeGette'



.. code:: ipython3

    Charles = counts['Charles Casper Stockham']
    Diana = counts["Diana DeGette"]
    Raymon = counts["Raymon Anthony Doane"]
    Charles, Diana, Raymon




.. parsed-literal::

    (85213, 272892, 11606)



.. code:: ipython3

    Charles_percent = (Charles/total)*100
    Charles_percent = round(Charles_percent,3)
    Diana_percent = (Diana/total)*100
    Diana_percent = round(Diana_percent,3)
    Raymon_percent = (Raymon/total)*100
    Raymon_percent = round(Raymon_percent,3)
    
    Charles_percent, Diana_percent, Raymon_percent




.. parsed-literal::

    (23.049, 73.812, 3.139)



.. code:: ipython3

    print("Election Results")
    print("-------------------------------------------------")
    print(f"Total Votes:                  {total}")
    print("-------------------------------------------------")
    print(f"Charles Casper Stockham :     {Charles_percent}%  ({Charles})")
    print(f"Diana DeGette :               {Diana_percent}%  ({Diana})")
    print(f"Raymon Anthony Doane :        {Raymon_percent}%  ({Raymon})")
    print("-------------------------------------------------")
    print(f"Winner:                       {winner}")
    print("-------------------------------------------------")


.. parsed-literal::

    Election Results
    -------------------------------------------------
    Total Votes:                  369711
    -------------------------------------------------
    Charles Casper Stockham :     23.049%  (85213)
    Diana DeGette :               73.812%  (272892)
    Raymon Anthony Doane :        3.139%  (11606)
    -------------------------------------------------
    Winner:                       Diana DeGette
    -------------------------------------------------
    

