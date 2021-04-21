# ChinaUnionBillService

1. Input specification description

<table>
<tr><td>Input parameter </td><td>Parameter type </td> <td>Restriction </td></tr>
<tr><td>planType  </td><td>String </td><td> only allows characters A, a, B, b </td></tr>
<tr><td>planFee </td><td> int </td><td> </td></tr>
<tr><td>talkTime </td><td> int </td><td> </td></tr>
<tr><td>flow </td><td> int </td><td> </td></tr>
<tr><td>callViewTime </td> <td>int </td> <td>callviewtime==0 </td></tr>
</table>

2. output specifications 

   The output parameters are “bill”, and the calculation formula of bill is:<br>
   Bill = (talkTime-talkTimeBench) * talkTimePer +(flow-flowBench) * flowPer + planFee<br>
   talkTime is the talk time consumed by the user, talkTimePer is the call charge per minute, flow is the traffic consumed by the user, flowPer is the charge per minute of traffic, talkTimeBench and flowBench are the free talk time and traffic in the package, and planFee is the user The basic package fee booked every month is shown in the table :<br>

<table><tr>
<td>planType</td> <td>planFee</td> <td>talkTimeBench</td> <td>flowBench </td><td>talkTime</td><td>Per flowPer</td></tr>
<tr><td>A </td><td>46</td> <td>50</td> <td>150</td> <td>0.25</td><td> 0.3</td></tr>
<tr><td>A </td><td>96 </td><td>96</td><td> 240</td> <td>0.15</td><td> 0.3</td></tr>
<tr><td>A </td><td>286 </td><td>286</td> <td>900</td><td> 0.15</td><td> 0.3</td></tr>
<tr><td>A </td><td>886</td></td> <td>3000</td> <td>3000</td> <td>0.15</td> <td>0.3</td></tr>
<tr><td>B </td><td>46</td><td> 120 </td><td>40</td> <td>0.25</td><td> 0.3</td></tr>
<tr><td>B </td><td>96 </td><td>450</td><td> 80</td> <td>0.15</td> <td>0.3</td></tr>
<tr><td>B </td><td>126 </td><td>680</td><td> 100</td> <td>0.15</td><td> 0.3</td></tr>
<tr><td>B </td><td>186 </td><td>1180</td><td> 150</td><td> 0.15</td> <td>0.3</td></tr>
<table>


3.  Description of Metamorphic relations<br>
   According to the specification of the program, the specific Metamorphic relations description can be obtained as shown in the following table.<br>

<table><tr><td>No.</td><td>R </td><td>Rf</td></tr>
<tr><td colspan="3">Type=A, planFee=46, 50<=talktime<=8000 & flow<=150,</td></tr>
<tr><td>MR1 </td><td>talktime_=talktime+1,(50<=talktime<=7999) </td><td>bill_=bill+0.25</td></tr>
<tr><td>MR2</td> <td>talktime_=2*talktime, (50<=talktime<=4000) </td><td>bill_>=bill</td></tr>
<tr><td colspan="3">2. Type=A, planFee=96, 96<=talktime<=8000 & flow<=240,</td></tr>
<tr><td>MR3 </td><td>talktime_=talktime+1,(96<=talktime<=7999)</td><td>bill_>bill+0.15</td></tr>
<tr><td>MR4</td><td> talktime_=2*talktime, (96<=talktime<=4000) </td><td>bill_>=bill</td></tr>
<tr><td colspan="3">3. Type=A, planFee=286, 286<=talktime<=8000 & flow<=900,</td></tr>
<tr><td>MR5</td> <td>talktime_=talktime+1,(286<=talktime<=7999) </td><td>bill_=bill+0.25</td></tr>
<tr><td>MR6 </td><td>talktime_=2*talktime, (286<=talktime<=4000)</td><td> bill_>=bill</td></tr>
<tr><td colspan="3">4. Type=A, planFee=886, 3000<=talktime<=8000 & flow<=3000,</td></tr>
<tr><td>MR7</td> <td>talktime_=talktime+1,(3000<=talktime<=7999) </td><td>bill_=bill+0.25</td></tr>
<tr><td>MR8</td><td> talktime_=2*talktime, (3000<=talktime<=4000) </td><td>bill_>=bill</td></tr>
<tr><td colspan="3">5. Type=B, planFee=46, talktime<=120 & 40<=flow<=1000,</td></tr>
<tr><td>MR9</td><td> flow_=flow+1,(40<=flow<=1000) </td><td>bill_>bill</td></tr>
<tr><td>MR10</td><td> flow_=2*flow, (40<=flow<=500)</td> <td>bill_>=bill</td></tr>
<tr><td colspan="3">6.Type=B, planFee=96, talktime<=450 & 80<=flow<=1000,</td></tr>
<tr><td>MR11 </td><td>flow_=flow+1,(80<=flow<=1000)</td><td> bill_>bill</td></tr>
<tr><td>MR12</td><td> flow_=2*flow, (80<=flow<=500) </td><td>bill_>=bill</td></tr>
<tr><td colspan="3">7. Type=B, planFee=126, talktime<=680 & 100<=flow<=1000,</td></tr>
<tr><td>MR13 </td><td>flow_=flow+1,(100<=flow<=1000) </td><td>bill_>bill</td></tr>
<tr><td>MR14</td> <td>flow_=2*flow, (100<=flow<=500)</td><td> bill_>=bill</td></tr>
<tr><td colspan="3">8. Type=B, planFee=186, talktime<=1180 & 150<=flow<=1000,</td></tr>
<tr><td>MR15</td><td> flow_=flow+1,(150<=flow<=1000)</td><td> bill_>bill</td></tr>
<tr><td>MR16</td> <td>flow_=2*flow, (150<=flow<=500) </td><td>bill_>=bill</td></tr>
<tr><td colspan="3">9. Type=A, planFee=286, talktime<=286 & flow<=900,</td></tr>
<tr><td>MR17</td><td> talktime_=talktime+1,</td> <td>bill_==bill</td></tr>
<tr><td colspan="3">10. Type=B, planFee=186, talktime<=1180 & flow<=150</td></tr>
<tr><td>MR18</td><td> talktime_=talktime-1,</td><td> bill_==bill</td></tr>
</table>
