# 86.7 Derivation of Sensitivity for Stock Options with Respect to Exercise Price

For a European call option on a non-dividend stock, the sensitivity can be shown as

$$\frac{\partial C_t}{\partial X} = -e^{-r\tau} N(d_2). \tag{86.29}$$

The derivation of (86.29) is

$$\frac{\partial C_t}{\partial X} = S_t \frac{\partial N(d_1)}{\partial X} - e^{-r\tau} N(d_2) - X e^{-r\tau} \frac{\partial N(d_2)}{\partial X}$$\n$$= S_t \frac{\partial N(d_1)}{\partial d_1} \frac{\partial d_1}{\partial X} - e^{-r\tau} N(d_2) - X e^{-r\tau} \frac{\partial N(d_2)}{\partial d_2} \frac{\partial d_2}{\partial X}$$\n$$= S_t \frac{1}{\sqrt{2\pi}} e^{-\frac{d_1^2}{2}} \cdot \frac{1}{\sigma_s \sqrt{\tau}} \cdot \left(-\frac{1}{X}\right) - e^{-r\tau} N(d_2)$$\n$$\quad - X e^{-r\tau} \left(\frac{1}{\sqrt{2\pi}} e^{-\frac{d_2^2}{2}} \cdot \frac{S_t}{X} \cdot e^{r\tau}\right) \frac{1}{\sigma_s \sqrt{\tau}} \cdot \left(-\frac{1}{X}\right)$$\n$$= \frac{1}{\sigma_s \sqrt{2\pi\tau}} e^{-\frac{d_1^2}{2}} \left(-\frac{S_t}{X}\right) - e^{-r\tau} N(d_2) - \frac{1}{\sigma_s \sqrt{2\pi\tau}} e^{-\frac{d_2^2}{2}} \left(-\frac{S_t}{X}\right)$$\n$$= -e^{-r\tau} N(d_2).$$

For a European put option on a non-dividend stock, the sensitivity can be shown as

$$\frac{\partial P_t}{\partial X} = e^{-r\tau} N(-d_2). \tag{86.30}$$

The derivation of (86.30) is

$$\frac{\partial P_t}{\partial X} = e^{-r\tau} N(-d_2) + X e^{-r\tau} \frac{\partial N(-d_2)}{\partial X} - S_t \frac{\partial N(-d_1)}{\partial X}$$\n$$= e^{-r\tau} (1 - N(d_2)) + X e^{-r\tau} \frac{\partial (1 - N(d_2))}{\partial d_2} \frac{\partial d_2}{\partial X} - S_t \frac{\partial (1 - N(d_1))}{\partial d_1} \frac{\partial d_1}{\partial X}$$\n$$= e^{-r\tau} (1 - N(d_2)) - X e^{-r\tau} \left(\frac{1}{\sqrt{2\pi}} e^{-\frac{d_2^2}{2}} \cdot \frac{S_t}{X} \cdot e^{r\tau}\right) \frac{1}{\sigma_s \sqrt{\tau}} \cdot \left(-\frac{1}{X}\right)$$\n$$\quad + S_t \frac{1}{\sqrt{2\pi}} e^{-\frac{d_2^2}{2}} \cdot \frac{1}{\sigma_s \sqrt{\tau}} \cdot \left(-\frac{1}{X}\right)$$