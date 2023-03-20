# Modified Momentum Transformer - IN PROCESS, DON'T FORK OR USE YET
## About
This is a table-driven version of Kieran et al's Momentum Transformer (https://github.com/kieranjwood/trading-momentum-transformer) which accompanies the paper [Trading with the Momentum Transformer: An Intelligent and Interpretable Architecture](https://arxiv.org/pdf/2112.08534.pdf). The objective of this repo is to make that important work accessible to a broader set of users through ease of implementation, iteration.

## How it's different
1. Whereas the original supported price series with daily periodicity, this version currently supports daily, 90-minute, 60-minute and 5-min data. Further it can be easily extended to support any data frequency / preriodicty.
2. Whereas the original version employed three configuration files (default, fixed model and parameter grid) and embedded some variables in the code, this version centralizes those variables in three files accessed by a single common function (config_vars()).
3. Whereas the original incorporated trading costs as a basis point charge on total cross-asset trade amount, new modules support explicit per asset / per transaction trading costs.
4. Whereas the original version used Keras' RandomSearch tuner to explore the hyperparamter grid, this version supports use of Keras' uses Hyperband tuner for traversing the multi-dimensional parameter space.
5. Whereas the original version was implemented in a series of python files executed from the command line, this version places those calls in an (iPython) file which can be configured to run against local or cloud resources.
6. Where as the original directory structure assumed a single implementation, the new structure assumes users will run multiple versions each of which will be stored in their own directory complete w/ experiment-specific settings, source code, input data and results.

## Using the code
1. To get / run data from the paper: Create a Nasdaq Data Link account to access the [free Quandl dataset](https://data.nasdaq.com/data/CHRIS-wiki-continuous-futures/documentation). This dataset provides continuous contracts for 600+ futures, built on top of raw data from CME, ICE, LIFFE etc. Then download the Quandl data with: `python -m data.download_quandl_data <<API_KEY>>`
2. To run data using closing equity prices for sample daily, 90-minute, 60-minute or 5-minute data...
3. Double-click the iPython notebook which will then walk you through creating the input features including changepoint detection (optional), running a model, reporting results. 

## References
Please cite Kieran et al's papers with:
```bib
@article{wood2021trading,
  title={Trading with the Momentum Transformer: An Intelligent and Interpretable Architecture},
  author={Wood, Kieran and Giegerich, Sven and Roberts, Stephen and Zohren, Stefan},
  journal={arXiv preprint arXiv:2112.08534},
  year={2021}
}

@article {Wood111,
	author = {Wood, Kieran and Roberts, Stephen and Zohren, Stefan},
	title = {Slow Momentum with Fast Reversion: A Trading Strategy Using Deep Learning and Changepoint Detection},
	volume = {4},
	number = {1},
	pages = {111--129},
	year = {2022},
	doi = {10.3905/jfds.2021.1.081},
	publisher = {Institutional Investor Journals Umbrella},
	issn = {2640-3943},
	URL = {https://jfds.pm-research.com/content/4/1/111},
	eprint = {https://jfds.pm-research.com/content/4/1/111.full.pdf},
	journal = {The Journal of Financial Data Science}
}
