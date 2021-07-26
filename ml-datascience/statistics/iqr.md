# IQR

Assuming data follows a gaussian distribution, the IQR covers the **range between the Q1 and Q3**. It's very easily to compute: $$\text{IQR} = \text{Q3} - \text{Q1}$$.

Once the IQR is known, we can classify as anomaly every value:

* Higher than $$Q3 + 1.5 \text{ IQR}$$
* Lower than $$Q1 - 1.5 \text{ IQR}$$

![Credit: Wikipedia](../../.gitbook/assets/image%20%2828%29.png)

### 

