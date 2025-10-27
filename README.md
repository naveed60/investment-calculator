# investment-calculator
To create an investment calculator, you'll need to define the inputs such as initial investment, interest rate, time period, and compounding frequency. Here's an example of how you can calculate the future value of an investment using compound interest:

Formula for Compound Interest:
𝐴
=
𝑃
×
(
1
+
𝑟
𝑛
)
𝑛
×
𝑡
A=P×(1+ 
n
r
​
 ) 
n×t
 
Where:

𝐴
A = Future Value (the amount of money accumulated after interest)
𝑃
P = Principal (the initial investment)
𝑟
r = Annual interest rate (decimal form, e.g., 5% as 0.05)
𝑛
n = Number of times the interest is compounded per year
𝑡
t = Time the money is invested or borrowed for, in years
Steps to Implement:
Input Fields:

Initial investment amount
Annual interest rate (in percentage)
Number of years
import React, { useState, useMemo } from 'react';
import { LineChart, Line, XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer } from 'recharts';
import { DollarSign, TrendingUp, Calendar, Percent } from 'lucide-react';

export default function InvestmentCalculator() {
  const [initialAmount, setInitialAmount] = useState(10000);
  const [monthlyContribution, setMonthlyContribution] = useState(500);
  const [years, setYears] = useState(10);
  const [returnRate, setReturnRate] = useState(7);
  const [compoundFrequency, setCompoundFrequency] = useState('monthly');

  const compoundingPeriods = {
    'annually': 1,
    'semi-annually': 2,
    'quarterly': 4,
    'monthly': 12,
    'daily': 365
  };

  const calculateInvestment = useMemo(() => {
    const r = returnRate / 100;
    const n = compoundingPeriods[compoundFrequency];
    const t = years;
    const P = initialAmount;
    const PMT = monthlyContribution;
    
    let chartData = [];
    let totalInvested = P;
    let balance = P;

Compounding frequency (e.g., annually, monthly, etc.)
Calculate Future Value:

Use the formula for compound interest to calculate the future value.
