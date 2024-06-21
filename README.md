# Part I (Analytical Option Formulae)

Consider the following European options:

*•* Vanilla call/put

*•* Digital cash-or-nothing call/put

*•* Digital asset-or-nothing call/put

Derive and implement the following models to value these options in Python:

1. **Black-Scholes model**

2. **Bachelier model**

3. **Black76 model**

4. **Displaced-diffusion model**

# Part II (Model Calibration)

On 1-Dec-2020, the S&P500 (SPX) index value was 3662.45, while the SPDR S&P500 Exchange Traded Fund (SPY) stock price was 366.02. The call and put option prices (bid & offer) over 3 maturities are provided in the spreadsheet:

*•* `SPX options.csv`

*•* `SPY options.csv`

The discount rate on this day is in the file: `zero_rates_20201201.csv`.

Calibrate the following models to match the option prices:

1. **Displaced-diffusion model**

2. **SABR model (fix $\beta = 0.7$)**

Plot the fitted implied volatility smile against the market data.

Report the model parameters:

1. **$\alpha, \beta$**

2. **$\alpha, \beta, \nu $**

And discuss how does change $\beta$ in the displaced-diffusion model and $\rho$, $\nu$​ in the SABR model affect the shape of the implied volatility smile.

# Part III (Static Replication)

Suppose on 1-Dec-2020, we need to evaluate an exotic European derivative expiring on 15-Jan-2021 which pays:

1. Payoff function:
   $$
   S^{1/3}_T + 1.5 \times \rm {log(\it S_T)} + 10.0
   $$
   

2. "Model-free" interated variance:
   $$
   \sigma^2_{MF}T = \Bbb {E}[\int_0^T {\sigma^2_t} \,{\rm d}t]
   $$
   

Determine the price of these 2 derivative contracts if we use:

1. Black-Scholes model (what $\sigma$ should we use?)

2. Bachelier model (what $\sigma$ should we use?)

3. Static-replication of European payoff (using the SABR model calibrated in the previous question)

# Part IV (Dynamic Hedging)

Suppose $S_0 = \$100, \sigma = 0.2, r=5\%,T = \frac{1}{12} year$, i.e. 1 month, and *K* = $100. Use a Black-Scholes model to simulate the stock price. Suppose we sell this at-the-money call option, and we hedge *N* times during the life of the call option. Assume there are 21 trading days over the month.

The dynamic hedging strategy for an option is 
$$
C_t = \phi_tS_t - \psi_tB_t
$$
where
$$
\phi_t = \frac{\partial C}{\partial S} = \Phi \left( \frac{\log \left( \frac{S_t}{K} \right) + \left( r + \frac{1}{2} \sigma^2 \right) (T - t)}{\sigma \sqrt{T - t}} \right),
$$


and
$$
\psi_t B_t = -K e^{-r(T - t)} \Phi \left( \frac{\log \left( \frac{S_t}{K} \right) + \left( r - \frac{1}{2} \sigma^2 \right) (T - t)}{\sigma \sqrt{T - t}} \right).
$$
Work out the hedging error of the dynamic delta hedging strategy by comparing the replicated position based on *ϕ* and *ψ* with the final call option payoff at maturity.

Use 50,000 paths in your simulation, and plot the histogram of the hedging error for *N* = 21 and *N* = 84.