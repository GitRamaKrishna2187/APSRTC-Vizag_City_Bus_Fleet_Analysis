**Executive view**



1\) Total City Buses = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric] ="Total Fleet Operated (Owned+Hired)")

2\) Active Routes = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="City Routes (Active)")

3\) Effective Fleet Operatng = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Effective Fleet (Operating)")

4\) Daily\_Passengers = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Avg Daily Passengers (Lakh)")

5\) KM Operated/Day = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Total KM Operated per Day (Lakh)")

6\) EPKM(Rs/Km) = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="EPKM – Earnings per KM (Rupees)")

7\) Daily Revenue = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]= "Avg Daily Revenue (Lakhs)")

**8) Fleet Utilization% =**

**VAR Effective= CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Effective Fleet (Operating)")**

**VAR Total=CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Total Fleet Operated (Owned+Hired)")**

**RETURN**

**DIVIDE(Effective,Total,0)\*100**

**9)Revenue\_BusType =** 

**VAR TotalRevenue = SUM('Daily\_Ops\_Log'\[Revenue\_INR])**

**VAR TotalBuses =** 

&#x20;   **CALCULATE(**

&#x20;       **DISTINCTCOUNT('Daily\_Ops\_Log'\[Bus\_Reg\_No]),** 

&#x20;       **ALLEXCEPT('Daily\_Ops\_Log', 'Daily\_Ops\_Log'\[Bus\_Type])**

&#x20;   **)**

**VAR CurrentBusTypeCount = DISTINCTCOUNT('Daily\_Ops\_Log'\[Bus\_Reg\_No])**



**RETURN**

**DIVIDE(TotalRevenue, TotalBuses, 0) \* CurrentBusTypeCount**

**10)Effective Fleet Operatng = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Effective Fleet (Operating)")**



**Bus Fleet Analysis**



1\) Maint\_Buses = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Buses Under Repair/Maintenance (Daily Avg)")

2\) Revenue/bus/day(rs) = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Revenue per Bus per Day (Rupees)")

3\) Km/Bus/Day (Avg) = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Avg KM per Bus per Day")

4\) **Fleet\_age>10 yrs =**

&#x20;    **SUMX('Bus\_Master',IF(year(TODAY())-'Bus\_Master'\[Year\_Manuf]>=10,1,0))**



**Depot Score card**



1)Bus Stops / Shelters = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Bus Stops / Shelters")

2)Cost/Km = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="CPKM – Cost per KM (Rupees)")

3)Revenue\_Growth\_YOY = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Revenue Growth YOY")

**4)EPKM Growth % =**

&#x20;           **Var A = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="EPKM – Earnings per KM (Rupees)" \&\&**

&#x20;                                                                                                  **Yearly\_Trend\_RTI\[Year]="2018-19")**

&#x20;           **Var B = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="EPKM – Earnings per KM (Rupees)" \&\&**

&#x20;                                                                                                  **Yearly\_Trend\_RTI\[Year]="2023-24")**

&#x20;           **Var EPKM =(DIVIDE(B-A,A,0))\*100**

&#x20;           **RETURN EPKM**

**5)Pax\_Recovery %(Post-Covid) =**

&#x20;          **Var A = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Avg Daily Passengers (Lakh)" \&\&**

&#x09;											**Yearly\_Trend\_RTI\[Year]="2020-21")**

&#x20;          **Var B = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Avg Daily Passengers (Lakh)" \&\&**

&#x09;											**Yearly\_Trend\_RTI\[Year]="2023-24")**

&#x20;          **Var Pax =(DIVIDE(B-A,A,0))\*100**

&#x09;   **RETURN Pax**

**6)Fleet CAGR % =**

&#x09;   **Var End\_Fleet\_Size = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Total Fleet Operated (Owned+Hired)"**

&#x09;											 **\&\& Yearly\_Trend\_RTI\[Year]="2023-24")**

&#x09;   **Var Beginning\_Fleet\_Size = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Total Fleet Operated (Owned+Hired)"**

&#x09;											 **\&\& Yearly\_Trend\_RTI\[Year]="2018-19")**

&#x09;   **Var CAGR =(DIVIDE(End\_Fleet\_Size,Beginning\_Fleet\_Size,0))**

&#x09;   **RETURN CAGR**

7\) Revenue\_Growth\_YOY = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Revenue Growth YOY")

**Routes,Revenue \& Operation**



1)GPS / AIS-140 Fitted Buses(%) = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="GPS / AIS-140 Fitted Buses (Pct)")

2)CO2 Emissions per Pax-KM (gms) = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="CO2 Emissions per Pax-KM (grams)")

3)ePOS Digital Ticketing % = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="ePOS Digital Ticketing (Pct)")

4)Avg\_Trip\_Delay(min) = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Avg Trip Delay (Minutes)")

5)Bus Breakdown Incidents per Day = CALCULATE(sum(Yearly\_Trend\_RTI\[Value]),Yearly\_Trend\_RTI\[Metric]="Bus Breakdown Incidents per Day")

**6)Breakdown rate = DIVIDE(CALCULATE(COUNT(Daily\_Ops\_Log\[Trip\_ID]),Daily\_Ops\_Log\[Breakdown]="Yes"),\[Total Trips],0)**

**7)Total Trips = count(Daily\_Ops\_Log\[Trip\_ID])**

**8)Trips on Time = CALCULATE(count(Daily\_Ops\_Log\[Trip\_ID]),Daily\_Ops\_Log\[Delay\_Min]<=5)**

**9)On-Time Performance % = divide(\[Trips on Time],\[Total Trips],0)\*100**

**10)Avg\_Route\_Length(km) = AVERAGE(Route\_Master\[Dist\_KM])**

**11)Highest Revenue Route = CALCULATE(MAX(Route\_Master\[Route\_No]),Route\_Master\[Rev\_Day\_INR]=max(Route\_Master\[Rev\_Day\_INR]))**

