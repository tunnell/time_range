==========
Time range
==========


.. image:: https://img.shields.io/pypi/v/time_range.svg
        :target: https://pypi.python.org/pypi/time_range

.. image:: https://img.shields.io/travis/tunnell/time_range.svg
        :target: https://travis-ci.org/tunnell/time_range

.. image:: https://readthedocs.org/projects/time-range/badge/?version=latest
        :target: https://time-range.readthedocs.io/en/latest/?badge=latest
        :alt: Documentation Status


.. image:: https://pyup.io/repos/github/tunnell/time_range/shield.svg
     :target: https://pyup.io/repos/github/tunnell/time_range/
     :alt: Updates

.. image:: https://pyup.io/repos/github/tunnell/time_range/python-3-shield.svg
     :target: https://pyup.io/repos/github/tunnell/time_range/
     :alt: Python 3
     
.. image:: https://api.codacy.com/project/badge/Grade/54ccc5b06b2142baade214ad0da62ac4
   :alt: Codacy Badge
   :target: https://app.codacy.com/app/tunnell/time_range?utm_source=github.com&utm_medium=referral&utm_content=tunnell/time_range&utm_campaign=badger

Methods for handling time range overlaps for scheduling, taxes, and physics applications.


* Free software: GNU General Public License v3
* Documentation: https://time-range.readthedocs.io.


Tutorial
--------


.. code:: ipython3

    import time_range as tr

Specify a year

.. code:: ipython3

    year = 2017

For this year, define all your trips by defining where they are and when
the trip started. This is an ordered list so the end date is inferred
from the next trip in the list. For the start date, the first number is
month, the second is the day, the third is the hour, and so forth.

.. code:: ipython3

    trips = ({'country': 'NL', 'start': (1, 1)},
     {'country': 'ES', 'start': (3, 4, 14, 0)},
     {'country': 'NL', 'start': (4, 11, 19, 50)},
     {'country': 'US', 'start': (5, 22, 12), 'state': 'NJ'},
     {'country': 'US', 'start': (6, 30, 12, 30), 'state': 'TX'},
     {'country': 'US', 'start': (7, 3, 16, 28), 'state': 'NJ'})
    


Determine your time distribution over the year as follows for just
working days:

.. code:: ipython3

    series = tr.time_distribution(trips=trips, year=2004)
    series




.. parsed-literal::

    working_day    251.0
    (NL, NL)        73.0
    (ES, ES)        26.0
    (US, NJ)       150.0
    (US, TX)         2.0
    dtype: float64



And your fraction of income in each place as follows:

.. code:: ipython3

    tr.fraction_of_year(trips=trips, year=2004, income=100000)




.. raw:: html

    <div>
    <style>
        .dataframe thead tr:only-child th {
            text-align: right;
        }
    
        .dataframe thead th {
            text-align: left;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>days</th>
          <th>fraction_of_year</th>
          <th>income</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>working_day</th>
          <td>251.0</td>
          <td>1.000000</td>
          <td>100000.000000</td>
        </tr>
        <tr>
          <th>(NL, NL)</th>
          <td>73.0</td>
          <td>0.290837</td>
          <td>29083.665339</td>
        </tr>
        <tr>
          <th>(ES, ES)</th>
          <td>26.0</td>
          <td>0.103586</td>
          <td>10358.565737</td>
        </tr>
        <tr>
          <th>(US, NJ)</th>
          <td>150.0</td>
          <td>0.597610</td>
          <td>59760.956175</td>
        </tr>
        <tr>
          <th>(US, TX)</th>
          <td>2.0</td>
          <td>0.007968</td>
          <td>796.812749</td>
        </tr>
      </tbody>
    </table>
    </div>



Lastly, if you're just curious about the working days of that year:

.. code:: ipython3

    tr.get_working_days(2013).head()




.. raw:: html

    <div>
    <style>
        .dataframe thead tr:only-child th {
            text-align: right;
        }
    
        .dataframe thead th {
            text-align: left;
        }
    
        .dataframe tbody tr th {
            vertical-align: top;
        }
    </style>
    <table border="1" class="dataframe">
      <thead>
        <tr style="text-align: right;">
          <th></th>
          <th>working_day</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th>2013-01-01</th>
          <td>False</td>
        </tr>
        <tr>
          <th>2013-01-02</th>
          <td>True</td>
        </tr>
        <tr>
          <th>2013-01-03</th>
          <td>True</td>
        </tr>
        <tr>
          <th>2013-01-04</th>
          <td>True</td>
        </tr>
        <tr>
          <th>2013-01-05</th>
          <td>False</td>
        </tr>
      </tbody>
    </table>
    </div>






Credits
-------

This package was created with Cookiecutter_ and the `audreyr/cookiecutter-pypackage`_ project template.

.. _Cookiecutter: https://github.com/audreyr/cookiecutter
.. _`audreyr/cookiecutter-pypackage`: https://github.com/audreyr/cookiecutter-pypackage


