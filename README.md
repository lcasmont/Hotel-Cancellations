# Hotel Cancellation Prediction

A Hotel Group was losing revenue and facing severe relocation costs due to an unpredictable surge in reservation cancellations, and blind overbooking tactics were damaging the brand. This project solves that by deploying a proactive machine learning pipeline in KNIME to flag high-risk bookings well before the guest's scheduled arrival. 

**The Metric That Matters Most**
In hotel revenue management, missing a true cancellation (resulting in an empty room and lost revenue) is far more expensive than a false alarm (which only costs a quick confirmation email)[cite: 1]. Therefore, our entire model selection prioritized **Recall (Sensitivity)** to ensure no high-risk booking slips through the cracks. 

**The Winning Model**
After testing Decision Trees and multiple ensemble setups, a **100-tree Random Forest** provided the optimal operational balance without wasting computing power.
* **Recall (Sensitivity):** 0.748
* **Precision:** 0.882
* **F1-Score:** 0.809

**Data Engineering & Key Features**
Raw data rarely tells the whole story, so we built custom variables to expose actual customer behavior:
* **Cancellation Ratio:** Our most critical feature. By calculating the proportion of a guest's past cancelled bookings against their total reservation history, we instantly identify serial cancelers. 
* **LengthOfStays:** Consolidating separate week and weekend night variables into one continuous block improved the Random Forest's performance. 
* **Cleaned Demographics:** We fixed data anomalies by forcing adult counts to a minimum of one, flooring float values for children, and binning baby counts into logical categories to tighten model accuracy.

**Real-World Business Impact**
The pipeline processes live reservation data and exports a daily risk ledger for front desk managers. Instead of applying punitive rules to every guest, the hotel can now trigger targeted interventions—like requesting a deposit only from high-risk guests, sending personalized check-in prompts, or confidently adjusting daily overbooking limits.
