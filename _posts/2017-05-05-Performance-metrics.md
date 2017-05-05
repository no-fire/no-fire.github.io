---
title: Performance metrics
layout: post
permalink: /performance-metrics/
source-id: 1ijDOZYA7JSo1IK0SsE07t-GeeNLd_WQroUG5matkeSw
published: true
---
# Context and inspiration

We have had a lot of success with convolution-based regression for predicting the turning speed of the robot based on a single RGB input image. Unfortunately, we don't expect that approach to generalize well to lines with sharp enough corners that they can leave the field of view of the camera. To solve that problem, we need some sort of recurrent approach, with LSTM (Long-Short Term Memory) networks being the most compelling option

# Results

## Convolution-only

<table>
  <tr>
    <td>Data source</td>
    <td>Training epochs</td>
    <td>Training loss</td>
    <td>Validation loss</td>
  </tr>
  <tr>
    <td>Office</td>
    <td>2500</td>
    <td>0.02-0.03</td>
    <td>0.02 - 0.03</td>
  </tr>
  <tr>
    <td>QEA Blob + Office</td>
    <td>425</td>
    <td>0.0048</td>
    <td>0.0039</td>
  </tr>
</table>


## Recurrent postprocessing

<table>
  <tr>
    <td>Data source</td>
    <td>Data type</td>
    <td>Training epochs</td>
    <td>Training loss</td>
    <td>Validation loss</td>
  </tr>
  <tr>
    <td>Office only</td>
    <td>Predicted cmd_vels</td>
    <td></td>
    <td></td>
    <td>0.02 - 0.03</td>
  </tr>
  <tr>
    <td>Office only</td>
    <td>x512 feature vectors</td>
    <td></td>
    <td></td>
    <td>0.02 - 0.03</td>
  </tr>
</table>


## An example from **validation data**

<table>
  <tr>
    <td>ID</td>
    <td>Image</td>
    <td>Human command</td>
    <td>Conv. prediction</td>
    <td>LSTM prediction</td>
  </tr>
  <tr>
    <td>41</td>
    <td></td>
    <td>0.000</td>
    <td>-0.001</td>
    <td>-0.002</td>
  </tr>
  <tr>
    <td>42</td>
    <td></td>
    <td>0.000</td>
    <td>-0.001</td>
    <td>-0.001</td>
  </tr>
  <tr>
    <td>43</td>
    <td></td>
    <td>0.000</td>
    <td>-0.003</td>
    <td>-0.001</td>
  </tr>
  <tr>
    <td>44</td>
    <td></td>
    <td>0.000</td>
    <td>0.019</td>
    <td>0.004</td>
  </tr>
  <tr>
    <td>45</td>
    <td></td>
    <td>0.000</td>
    <td>0.088</td>
    <td>0.081</td>
  </tr>
  <tr>
    <td>46</td>
    <td></td>
    <td>0.000</td>
    <td>0.013</td>
    <td>0.001</td>
  </tr>
  <tr>
    <td>47</td>
    <td></td>
    <td>0.104</td>
    <td>0.019</td>
    <td>0.007</td>
  </tr>
  <tr>
    <td>48</td>
    <td></td>
    <td>0.097</td>
    <td>-0.081</td>
    <td>-0.083</td>
  </tr>
  <tr>
    <td>49</td>
    <td></td>
    <td>0.034</td>
    <td>-0.013</td>
    <td>-0.005</td>
  </tr>
  <tr>
    <td>50</td>
    <td></td>
    <td>0.107</td>
    <td>-0.041</td>
    <td>-0.037</td>
  </tr>
  <tr>
    <td>51</td>
    <td></td>
    <td>0.179</td>
    <td>-0.027</td>
    <td>-0.020</td>
  </tr>
  <tr>
    <td>52</td>
    <td></td>
    <td>0.166</td>
    <td>-0.001</td>
    <td>-0.001</td>
  </tr>
  <tr>
    <td>53</td>
    <td></td>
    <td>0.129</td>
    <td>-0.001</td>
    <td>-0.001</td>
  </tr>
  <tr>
    <td>54</td>
    <td></td>
    <td>0.129</td>
    <td>-0.001</td>
    <td>-0.001</td>
  </tr>
  <tr>
    <td>55</td>
    <td></td>
    <td>0.127</td>
    <td>0.002</td>
    <td>-0.001</td>
  </tr>
  <tr>
    <td>56</td>
    <td></td>
    <td>0.127</td>
    <td>0.006</td>
    <td>0.000</td>
  </tr>
  <tr>
    <td>57</td>
    <td></td>
    <td>0.039</td>
    <td>0.058</td>
    <td>0.044</td>
  </tr>
  <tr>
    <td>58</td>
    <td></td>
    <td>0.117</td>
    <td>0.089</td>
    <td>0.084</td>
  </tr>
</table>


## An example from **training data**

<table>
  <tr>
    <td>ID</td>
    <td>Image</td>
    <td>Human command</td>
    <td>Conv. prediction</td>
    <td>LSTM prediction</td>
  </tr>
  <tr>
    <td>340</td>
    <td></td>
    <td>-0.074</td>
    <td>-0.071</td>
    <td>-0.077</td>
  </tr>
  <tr>
    <td>341</td>
    <td></td>
    <td>-0.124</td>
    <td>-0.125</td>
    <td>-0.132</td>
  </tr>
  <tr>
    <td>342</td>
    <td></td>
    <td>-0.164</td>
    <td>-0.166</td>
    <td>-0.162</td>
  </tr>
  <tr>
    <td>343</td>
    <td></td>
    <td>0.000</td>
    <td>-0.001</td>
    <td>-0.004</td>
  </tr>
  <tr>
    <td>344</td>
    <td></td>
    <td>0.000</td>
    <td>-0.001</td>
    <td>-0.002</td>
  </tr>
  <tr>
    <td>345</td>
    <td></td>
    <td>-0.049</td>
    <td>-0.052</td>
    <td>-0.057</td>
  </tr>
  <tr>
    <td>346</td>
    <td></td>
    <td>-0.059</td>
    <td>-0.058</td>
    <td>-0.065</td>
  </tr>
  <tr>
    <td>347</td>
    <td></td>
    <td>-0.206</td>
    <td>-0.207</td>
    <td>-0.207</td>
  </tr>
  <tr>
    <td>348</td>
    <td></td>
    <td>-0.156</td>
    <td>-0.151</td>
    <td>-0.156</td>
  </tr>
  <tr>
    <td>349</td>
    <td></td>
    <td>0.000</td>
    <td>-0.001</td>
    <td>-0.004</td>
  </tr>
  <tr>
    <td>350</td>
    <td></td>
    <td>0.000</td>
    <td>-0.001</td>
    <td>-0.003</td>
  </tr>
  <tr>
    <td>351</td>
    <td></td>
    <td>-0.122</td>
    <td>-0.107</td>
    <td>-0.113</td>
  </tr>
  <tr>
    <td>352</td>
    <td></td>
    <td>-0.300</td>
    <td>-0.298</td>
    <td>-0.306</td>
  </tr>
  <tr>
    <td>353</td>
    <td></td>
    <td>-0.300</td>
    <td>-0.308</td>
    <td>-0.292</td>
  </tr>
  <tr>
    <td>354</td>
    <td></td>
    <td>-0.269</td>
    <td>-0.288</td>
    <td>-0.260</td>
  </tr>
  <tr>
    <td>355</td>
    <td></td>
    <td>0.300</td>
    <td>0.314</td>
    <td>0.273</td>
  </tr>
</table>


