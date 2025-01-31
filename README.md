# XGBoost-for-Revenue-Optimization-via-Strategic-Couponing
Leveraging Machine Learning for Revenue Optimization via Strategic Couponing (University Class Project)


## Introduction
Many customers order only once in an online store. There are several reasons why they don’t place another order. To counteract this, online retailers use various customer loyalty measures. One measure, for example, is to send coupons sometime after an initial order has been placed. The intention is to encourage the customer to make a follow-up purchase. Even though the vouchers don’t cost the online retailer anything directly, it is not a good solution to send all customers a discount voucher: Some customers would make a follow-up purchase even without a voucher. In this case, a redeemed discount means less revenue for the online retailer. Therefore, it is crucial to devise a more targeted approach for distributing these vouchers.

## Task
The task at hand involves constructing a predictive model that leverages various features associated with a customer’s initial order. The objective is to determine whether a €5.00 voucher should be issued to a
specific customer. The model should be designed to predict if a customer will place a follow-up purchase within 90 days following their initial purchase. This information is represented by the target90 variable in the dataset. Each customer who is predicted to not place a subsequent order will be sent a voucher.

Empirical analyses by the media retailer have shown that for 25% of the churning customers, the voucher triggers a purchase with an average order value of €10. So if a voucher is sent to a customer who would not have bought again, revenue increases by an average of €1.25. Conversely, sending a voucher to a customer who would have placed an order anyway results in a revenue loss equivalent to the voucher value of €5. For customers who don’t receive a voucher, there is no impact on revenues.

The model’s performance is evaluated based on the expected revenue across all customers in a given dataset. This is computed by considering the model’s predictions in conjunction with the associated costs and revenues. It’s crucial to note that the model’s effectiveness is directly tied to its ability to maximize this expected revenue. Hence, the model should be optimized with this specific goal in mind.
