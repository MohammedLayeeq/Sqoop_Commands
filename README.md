# Sqoop_Commands
Sqoop Commands
Step 15 : Converting Data to UCID & Cohort Level 
(woolworths.development.wns_ma_cvm_campaign_int_voucher_metrics)

data_hierarchy_level
ucid	
campaign_name	
offer
cohort_name
redeemer_ind	
no_of_vouchers_issued	
no_of_redeemed_vouchers	
voucher_cost
redeemption_cost
email_status
sms_status

Combining Subqueries:
All three subqueries are combined using UNION ALL to create a unified result set.
Table Population:
The selected and transformed columns, as well as the calculated status descriptions, are used to populate the new table wns_ma_cvm_campaign_int_voucher_metrics.
In summary, this script creates a new table wns_ma_cvm_campaign_int_voucher_metrics by aggregating and transforming data from the wns_ma_cvm_campaign_int4 table into different hierarchy levels: Company, Offer Type, and Cohort. The resulting table contains various metrics related to vouchers, redemptions, costs, and status descriptions for each data hierarchy level. 

Step 16 : Converting Data to UCID & Cohort Level 
(woolworths.development.wns_ma_cvm_campaign_int5)

data_hierarchy_level
business_unit
ucid
campaign_name
offer
cohort_name
channel
tg_cg_ind

Combining Subqueries:
All three subqueries are combined using UNION ALL to create a unified result set.

Table Population:
The selected columns from the subqueries are used to populate the new table wns_ma_cvm_campaign_int5.

In summary, this script creates a new table wns_ma_cvm_campaign_int5 by selecting columns related to data hierarchy levels (Company, Offer Type, Cohort), along with other details such as business_unit, ucid, campaign_name, offer, cohort_name, channel, and tg_cg_ind. The resulting table contains a combined view of data based on these hierarchy levels.

Step 17 : Adding Demographics Info 
(woolworths.development.wns_ma_cvm_customer_base_table)
data_hierarchy_level
business_unit
ucid
campaign_name
offer
cohort_name
channel
tg_cg_ind
app_ind	
customer_cohort
age_band
derived_race
gender
macro_segment
micro_segment
hhi_band
Table Population:
The selected columns from both tables, as well as the derived columns with renamed values, are used to populate the new table wns_ma_cvm_customer_base_table.
In summary, this script creates a new table wns_ma_cvm_customer_base_table by joining data from the wns_ma_cvm_campaign_int5 table with the wns_ma_cvm_demographics table based on the ucid column. The resulting table will contain a combination of customer base information and demographic attributes, with some columns renamed for consistency
Step 17 : Adding Transaction Details to Base Table
(woolworths.development.wns_ma_cvm_customer_base_table)
data_hierarchy_level
business_unit
ucid
campaign_name
offer
cohort_name
channel
tg_cg_ind
app_ind
customer_cohort
age_band
derived_race
gender
macro_segment
micro_segment
hhi_band
tran_id
business_unit_name
bar_ucid
location_no
tran_date
tran_no
till_no
total_spent
redeemed_date
Table Population:
The selected columns from both tables (a and b), as well as the redeemed_date from the subquery (c), are used to populate the new table wns_ma_cvm_cust_tran_base_table.
In summary, this script creates a new table wns_ma_cvm_cust_tran_base_table by joining data from the wns_ma_cvm_customer_base_table and wns_ma_cvm_bar_transaction_data tables based on the ucid and business_unit columns. Additionally, it joins the transaction data with information about redeemed vouchers from the wns_ma_cvm_redeemed_voucher_table. The resulting table will contain a combination of customer and transaction data along with redeemed voucher details.

Step 18 : Adding additional KPI metrics
(woolworths.development.wns_ma_cvm_campaign_cust_metrics)
data_hierarchy_level
campaign_program_ind
campaign_program_name
tg_cg_ind
product_hierarchy_level
product_hierarchy_name
cohort_name
channel
offer
email_status
sms_status
customer_cohort
age_band
derived_race
gender
macro_segment
micro_segment
hhi_band
redeemer_ind
app_ind
ucid
no_of_vouchers_issued
no_of_redeemed_vouchers
voucher_cost
redeemption_cost
campaign_period_customer_count
campaign_period_revenue_vat_incl
campaign_period_revenue_vat_excl
campaign_period_units
campaign_period_visits
redeemed_basket_revenue_vat_incl
redeemed_basket_revenue_vat_excl
redeemed_basket_units
redeemed_visits
pre_6M_period_customer_count
pre_6M_period_revenue_vat_incl
pre_6M_period_revenue_vat_excl
pre_6M_period_units
pre_6M_period_visits
pre_12M_period_customer_count
pre_12M_period_revenue_vat_incl
pre_12M_period_revenue_vat_excl
pre_12M_period_units
pre_12M_period_visits
ly_period_customer_count
ly_period_revenue_vat_incl
ly_period_revenue_vat_excl
ly_period_units
ly_period_visits

Table Population:
The selected columns, along with the calculated KPIs, are used to populate the new table wns_ma_cvm_campaign_cust_metrics.
In summary, this script creates a new table wns_ma_cvm_campaign_cust_metrics by selecting columns and calculating KPIs from multiple source tables (wns_ma_cvm_cust_tran_base_table, wns_ma_cvm_campaign_details, wns_ma_cvm_campaign_int_voucher_metrics) and performing joins and aggregations. The resulting table will contain a comprehensive set of metrics and details related to campaign performance and customer behavior.

Step 19 : Adding additional KPI metrics
(woolworths.development.wns_ma_genesis_cvm_campaign_output)
data_hierarchy_level
campaign_program_ind
campaign_program_name
tg_cg_ind
app_ind
product_hierarchy_level
product_hierarchy_name
cohort_name
channel
offer
email_status
sms_status
customer_cohort
age_band
derived_race
gender
macro_segment
micro_segment
hhi_band
redeemer_ind
total_customer_count
campaign_period_customer_count
campaign_period_revenue_vat_incl
campaign_period_revenue_vat_excl
campaign_period_units
campaign_period_visits
redeemed_basket_revenue_vat_incl
redeemed_basket_revenue_vat_excl
redeemed_basket_units
redeemed_visits
pre_6M_period_customer_count
pre_6M_period_revenue_vat_incl
pre_6M_period_revenue_vat_excl
pre_6M_period_units
pre_6M_period_visits
pre_12M_period_customer_count
pre_12M_period_revenue_vat_incl
pre_12M_period_revenue_vat_excl
pre_12M_period_units
pre_12M_period_visits
ly_period_customer_count
ly_period_revenue_vat_incl
ly_period_revenue_vat_excl
ly_period_units
ly_period_visits
no_of_vouchers_issued
no_of_redeemed_vouchers
voucher_cost
redeemption_cost

Table Population:
The selected columns and aggregated metrics are used to populate the wns_ma_genesis_cvm_campaign_output table.
In summary, this script calculates various campaign metrics and aggregates them for different periods and attributes. It then inserts the calculated data into the wns_ma_genesis_cvm_campaign_output table. This table will contain a comprehensive set of campaign-related metrics and information for reporting and analysis.

In summary, this SQL script inserts aggregated metrics and attributes from the wns_ma_cvm_campaign_cust_metrics table into the wns_ma_genesis_cvm_campaign_output table. The aggregation is performed based on various columns and includes calculations for different campaign periods and customer behaviors. The commented-out section suggests the possibility of joining data from another table (wns_ma_cvm_voucher_metrics), although it's currently not active in the script.
