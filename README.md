# Electric-vehicle-analysis

Provide Insights to an Automotive company on Electric vehicles launch in India a challenge provide by code basics 

Domain:  Automotive

AtliQ Motors is an automotive giant from the USA specializing in electric vehicles (EV). In the last 5 years, their market share rose to 25% in electric and hybrid vehicles segment in North America. As a part of their expansion plans, they wanted to launch their bestselling models in India where their market share is less than 2%. Bruce Haryali, the chief of AtliQ Motors India wanted to do a detailed market study of existing EV/Hybrid market in India before proceeding further. Bruce gave this task to the data analytics team of AtliQ motors and Peter Pandey is the data analyst working in this team. 

Task: 

Imagine yourself as Peter Pandey and perform the following tasks. 

1.Begin your analysis by referring to the ‘primary_and_secondary_questions.pdf’. You can use any tool of your choice (Python, SQL, PowerBI, Tableau, Excel, PowerPoint) to analyze and answer these questions. More instructions 
  are provided in this document. 
2.Design a dashboard with your metrics and analysis. The dashboard should be self-explanatory and easy to understand. 
  You can use additional data based on your own research to support your recommendations and provide more insights. 

Import the necessary file into a business tool of your choice (such as Power BI, SQL, Python Notebook, or Tableau).

Steps to Follow:
1.Exploratory Data Analysis (EDA)
2.Data Preprocessing
3.Data Validation
4.Creating Key Metrics and DAX Measures
5.Visualization

"Since I completed this project using Power BI, I’ll guide you through the approach I followed in Power BI:"
-------

Next comes data modeling, where I connected the dimension and fact tables to build the report in Power BI.

![Screenshot (693)](https://github.com/user-attachments/assets/dd69b9f1-7480-4d2c-91ba-cb4a70612958)

-------

I created DAX measures relevant to the automotive domain, such as Penetration Rate, Compound Annual Growth Rate (CAGR), and more.

--Penetration Rate:This measure calculates the penetration rate of electric vehicles within a region or market
formula: Penetration Rate =  (Electric Vehicles Sold / Total Vehicles Sold) * 100  

DIVIDE(
    SUM(EV_Sales[EV Units Sold]), 
    SUM(Total_Sales[Total Units Sold]), 
    0
) * 100

--Year-over-Year Growth (YoY): To track the year-over-year growth of electric vehicle sales.
formula: IF(
    ISBLANK([Total EV Sales Last Year]), 
    BLANK(), 
    DIVIDE([Total EV Sales] - [Total EV Sales Last Year], [Total EV Sales Last Year], 0) * 100
)

--Compound Annual Growth Rate (CAGR): To calculate the annual growth rate of sales over a period of time
formula:       CAGR = [(Ending Value / Beginning Value) ** 1/n] -1

CAGR  = 
VAR StartValue = CALCULATE([total sells], 'dim_date'[fiscal_year] = 2022)
VAR EndValue = CALCULATE([total sells], 'dim_date'[fiscal_year] = 2024)
VAR NumberOfYears = 2
RETURN 
IF(
    StartValue > 0,
    ( (EndValue / StartValue) ^ (1 / NumberOfYears) ) - 1,
    BLANK()
)


--Total EV Sales: This simple measure calculates the total sales of electric vehicles.
Formula: Total EV Sales =  SUM(EV_Sales[EV Units Sold])


-- Top N States by Penetration Rate: To rank the top N states based on their EV penetration rate.
Formula 
Top N States by Penetration Rate =  TOPN(5, ALL(State), [Penetration Rate], DESC)

--------------

After creating all the required DAX measures, the next step is to define the key metrics that will drive the analysis and insights. These metrics serve as the foundation for creating impactful visuals in Power BI.

Check out the live dash board link 🔗

https://app.powerbi.com/view?r=eyJrIjoiYWNmY2Y4YTctZGM5Yy00NDBlLWJjZGEtZDM4N2EzNzcyNjU0IiwidCI6ImM2ZTU0OWIzLTVmNDUtNDAzMi1hYWU5LWQ0MjQ0ZGM1YjJjNCJ9





![Screenshot (691)](https://github.com/user-attachments/assets/e4818ed1-a1cc-4683-8a6f-19ffebb4042d)


![Screenshot (692)](https://github.com/user-attachments/assets/daa18fda-ecb6-4468-9ed8-72c701206612)



All files related to this project, including presentation slides, will be attached. Feel free to check them out!





