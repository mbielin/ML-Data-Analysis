# Datasheet Template

As far as you can, complete the model datasheet. If you have got the data from the internet, you may not have all the information you need, but make sure you include all the information you do have. 

## Motivation

Purpose of Creation: The dataset was created to analyze and predict the future lesson participation of swim club members, with the goal of improving membership retention, class planning, and personalized offerings.
Creator: The dataset was obtained from a swim club company, representing records of member participation over a 5-year span across multiple locations. It was created internally by the swim club’s data team.
Funding: The dataset was created and maintained by the swim club company for internal business purposes, and no external funding was involved.

 
## Composition

Instances Representation: The dataset comprises records of swim club members, detailing their participation in lessons (e.g., PreSchool and Academy classes) and various discounts applied during their membership.
Number of Instances: The dataset includes thousands of instances appox 67K representing individual members. The exact count varies, with members categorized by whether they are current members or leavers.
Missing Data: Some lesson columns and member discount details may have missing or zero values, particularly for members who did not participate in specific lessons or were not eligible for certain discounts.
Confidentiality: The dataset does not include personal identifiers beyond anonymized or generalized information like age at lesson and membership status. However, care should still be taken to avoid accidental exposure of sensitive information, particularly regarding membership details and discount eligibility.

## Collection process

Data Acquisition: The data was collected from the swim club’s internal membership and lesson tracking systems.
Sampling Strategy: The dataset reflects all recorded member activities within the company’s operations and does not represent a sample. It captures the full member base over a 5-year period.
Time Frame: The data covers swim club operations for the last five years, providing insight into both current and former members across different club locations.

## Preprocessing/cleaning/labelling

Preprocessing Steps: The dataset underwent several preprocessing steps, including:
Variance to Median (VTM) Calculation: For lessons, the variance to the median was computed to capture how individual members deviated from typical lesson participation.
Group-specific Ceilings: Future lessons were capped using the 90th percentile of lessons within specific age groups.
Handling Missing Values: Missing values in lesson columns were imputed with zeroes or excluded from specific calculations, depending on their context.
Raw Data Retention: The original raw data remains accessible for unanticipated future analysis or uses.
 
## Uses

Other Possible Uses: The dataset can be used for other tasks such as:
Member retention analysis
Personalized recommendation systems for future lessons
Financial forecasting for class occupancy and revenue
Considerations for Use: Since the data captures sensitive business and customer behavior, it is important to ensure that predictive models built from this data do not introduce biases or perpetuate unfair treatment based on age or membership status. Dataset consumers should ensure ethical use and avoid reinforcing stereotypes in membership analysis or marketing.
Tasks to Avoid: The dataset should not be used for tasks that involve customer profiling beyond the swim club’s domain or for any purposes that could expose member details without consent.

## Distribution

Distribution: The dataset has been shared internally within the company. It has not been distributed externally and remains proprietary to the swim club.
Copyright and Licensing: The dataset is subject to the swim club company’s internal data governance policies and may not be distributed without explicit permission. There are no external intellectual property licenses or terms of use applied to the dataset.

## Maintenance

Maintained By: The swim club company’s internal data team is responsible for maintaining and updating the dataset as needed for ongoing analysis and reporting.

