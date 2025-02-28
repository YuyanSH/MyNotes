
## Page 1
- 老师、同学们，大家下午好，很荣幸在这里进行展示，人类的身体复杂而多变，那么我们如何能够清楚地观察我们身体的内部信息呢？这正是我今天要介绍的内容：Dynamic Light Scattering Imaging (DLSI) in Biomedical Applications
- Good afternoon, teachers and fellow students. It's my honor to be here. The human body is complex and ever-changing. So, how can we clearly observe the internal information of our bodies? This is exactly what I will be introducing today: Dynamic Light Scattering Imaging (DLSI) in Biomedical Applications.
## Page 2 Contents
- 我的介绍包含一下几个部分，先是对技术背景以及原理的介绍，然后介绍实验部分，然后展示实验结果，之后介绍一下该技术的具体应用，最后是文章的总结与展望。
- My presentation consists of several sections. First, I will introduce the technological background and principles. Next, I will describe the experimental part, followed by displaying the experimental results. After that, I will discuss the specific applications of this technology. Finally, I will conclude with a summary and future outlook of the study.

## Page 3 Introduction to Traditional Techniques
- 当光照射到生物组织后会发生散射，如果能够接受散射的光，则会形成散斑，我们可以通过分析散斑来获取生物组织的内部信息比如血流。Common techniques include Laser Speckle Contrast Imaging (LSCI) and Laser Doppler Flowmetry (LDF) . 我们都有过这样的经历，当一辆车鸣着喇叭朝我们驶来时，我们听到的声音会越来越尖锐，也就是波的频率会随着观察距离的改变而改变，这就是多普勒现象，LDF正是利用了这个原理来分析血流的信息。对于LSCI，当同一束激光照射到不同的表面时，不同表面反射或者散射光到达成像面时走的光程不同，这样会发生干涉，形成干涉图样，我们称为散斑，我们可以通过分析散斑来获取血流信息。However, these techniques have limitations ,such as insufficient accuracy, overly simplified models and data interpretation errors.
- When light is projected onto biological tissues, it scatters, and if the scattered light is captured, it forms speckle patterns. By analyzing these speckles, we can obtain internal information about biological tissues, such as blood flow. Common techniques include Laser Speckle Contrast Imaging (LSCI) and Laser Doppler Flowmetry (LDF). We all have experienced this. When a car approaches us honking its horn, the sound we hear becomes increasingly shrill, meaning the frequency of the wave changes with the distance observed—this is the Doppler effect. LDF utilizes this principle to analyze information about blood flow. For LSCI, when the same laser beam illuminates different surfaces, the light paths taken by the reflected or scattered light to the imaging plane vary, causing interference and forming an interference pattern known as speckles. We can analyze these speckles to obtain information about blood flow. However, these techniques have limitations, such as insufficient accuracy, overly simplified models, and data interpretation errors.

## Page 4 What is DLSI?
- To address these issues , the authors developed the DLSI techniques. 这张图就是DLSI成像技术的示意图， 对激光进行准直以及偏振处理后，照射到成像组织上，用高速CMOS相机捕获经成像组织反射以及散射的光信号，and through improved models and data analysis, it provides more accurate measurements of blood flow in complex tissue environments.
- To address these issues, the authors developed the DLSI technique. This image is an illustration of the DLSI imaging technology. After collimating and polarizing the laser, it is directed onto the target tissue, and a high-speed CMOS camera captures the reflected and scattered light signals from the tissue. Through improved models and data analysis, it provides more accurate measurements of blood flow in complex tissue environments.

## Page 5 principle of DLSI

- 接下来介绍DLSI的原理。DLSI的原理基于对散斑强度时间自相关函数的建模和测量。
  这是文中给出的散斑强度时间自相关函数，其中β反映speckle的动态相干性，g1 (τ)是电场相关函数，反映散射粒子运动的动态，考虑到测量噪声的影响，作者添加了一个常数C，表示测量噪声的偏移量。
  g1 (τ)表达式是这个，τ_c表示相关时间，很明显相关时间越小，粒子运动速度越快，粒子散射越剧烈。n描述不同的散射和运动类型：
  n = 0.5 :multiple light scattering and unordered motion(MUn)
  n = 1 : single light scattering and unordered motion/multiple
            light scat tering and ordered motion(SU/MOn)
  n = 2 : single scattering and ordered motion(SOn)
  后面的实验结果会告诉我们不同的动态模式适用于不同区域。
  DLSI对散斑强度时间自相关函数的建模主要就是基于这些公式。
- Next, let's discuss the principles of DLSI. The principle of DLSI is based on the modeling and measurement of the speckle intensity temporal autocorrelation function. This is the speckle intensity temporal autocorrelation function provided in the article, where β reflects the dynamic coherence of the speckle, and g1(τ) is the electric field correlation function, reflecting the dynamics of the scattering particles' movement. Considering the impact of measurement noise, the authors added a constant C to represent the offset due to measurement noise.
  The expression for g1(τ) is as follows, where τ_c represents the correlation time. Clearly, the smaller the correlation time, the faster the particle movement and the more intense the scattering. The parameter n describes different types of scattering and motion:
  - n = 0.5: multiple light scattering and unordered motion (MUn)
  - n = 1: single light scattering and unordered motion/multiple light scattering and ordered motion (SU/MOn)
  - n = 2: single scattering and ordered motion (SOn)
  Subsequent experimental results will tell us which dynamic models are suitable for different regions.
  The modeling of the speckle intensity temporal autocorrelation function in DLSI is primarily based on these formulas.

## Page 6 Experimental Section

- 接下来介绍实验部分。本文的实验包含这几个部分，首先需要对经生物组织反射或散射的散斑进行成像也就是接受散斑信号，然后根据接收到的散斑信息对强度时间自相关函数进行计算，
  之后再对计算得到的强度时间自相关函数与文中给出的模型以及基础模型进行拟合，然后再对模型进行测试来确定适合拟合大脑不同区域的最佳模型，最后用拟合后的模型计算出的相关时间计算相对血流变化，这样就可以得到血液流动的信息。
- Next, let's delve into the experimental section of the paper. The experiments described involve several key steps. Initially, imaging of the speckle patterns, which are reflections or scatterings from biological tissues, is conducted to capture the speckle signals. Then, based on the captured speckle information, the intensity temporal autocorrelation function g2(tau) is calculated. 
  Subsequently, the calculated  g2(tau) is fitted against the models provided in the article, along with fundamental models, to determine the best fit. The models are then tested to identify the most suitable model for fitting different regions of the brain. Finally, the correlation times derived from the fitted models are used to calculate relative changes in blood flow, thereby providing information about blood circulation.


## Page 7 Imaging

- 在成像部分，DLSI对帧率的要求是很高的，这张图展示了DLSI所需要的最小帧率与相关时间以及粒子散射程度的关系及帧率对模型拟合优度( R^2 )的影响。
  图a的这一部分的曲线急速下降，显示了在粒子散射剧烈的区域例如小血管中的高速血流中，需要更高的采样率来捕获动态。
  曲线向右延伸进入标记为“Small vessels and parenchyma”的红色区域，这些区域的相关时间更长，血流流速较慢，帧率需求低。
  图b的这一部分表示颜色越接近上方的颜色，拟合优度越好，看这几幅图，很明显，帧率低的时候，只有少部分血流流速较慢的部分拟合优度较好，而当帧率很高的时候，整个区域的拟合优度都很好。
- In the imaging section, DLSI requires a high frame rate. This figure illustrates the relationship between the minimum frame rate required by DLSI and the correlation time, and the degree of particle scattering, as well as the impact of frame rate on the goodness of fit (R - squared) of the model.
  In part a of the figure, the curve drops sharply, indicating that in areas with intense particle scattering, such as high-speed blood flow in small vessels, a higher sampling rate is required to capture the dynamics. The curve extends to the right into the red area marked "Small vessels and parenchyma," where the correlation times are longer, the blood flow is slower, and the frame rate requirements are lower.
  Part b of the figure shows that the closer the color is to the top of the color scale, the better the goodness of fit. From these images, it is clear that at low frame rates, only the areas with slower blood flow have better fit quality, whereas at high frame rates, the goodness of fit is high across the entire area.


## Page 8 Intensity correlation & Model fitting

- 左半部分介绍对强度时间自相关函数的计算，首先需要对图像进行拼接与去除重叠部分，其次还需要减去相机的黑电平以减少相机本身的噪声的影响。然后根据这个公式计算散斑强度自相关函数，
  I表示不同时间的散斑强度，t是当前帧对应的时间，τ是时间滞后值，括号表示在总观察时间内对强度求平均。
  对模型进行拟合时，使用的是非线性最小二乘拟合算法，为避免拟合伪影，采用自适应约束拟合范围的方法，当然，为了提高拟合结果的普遍性，需要对时间强度自相关函数曲线进行“掐头去尾”。
- The left half of the section discusses the calculation of the intensity temporal autocorrelation function. Initially, images must be stitched together and overlapping parts removed, followed by the subtraction of the camera's black level to minimize the influence of intrinsic camera noise. The speckle intensity autocorrelation function is then calculated using this formula:
 
  Here, \( I \) represents the speckle intensity at different times, \( t \) is the time corresponding to the current frame, \( \tau \) is the time lag, and the brackets indicate averaging over the total observation time.
  When fitting the model, a nonlinear least squares fitting algorithm is used. To avoid fitting artifacts, an adaptive constraint fitting range method is employed. Moreover, to enhance the generality of the fitting results, the intensity temporal autocorrelation function curve is "trimmed," meaning the ends of the curve are excluded from the fitting process to ensure more reliable and generalizable outcomes.

## Page 9 Model testing with the F test & Blood flow

- 之后对拟合的模型进行F检验，F检验的过程，目的以及检验准则是这样的，当然，最主要的目的就是确定适合拟合大脑不同区域的最佳模型。
  之后用合适的模型计算真实情况下的血液流动情况，比如中风状态下的血流速度。公式是这个
- Subsequent to the model fitting, the F-test is conducted. The process and purpose of the F-test, along with the testing principle, are as follows. Primarily, the main goal is to determine the best model suitable for fitting different regions of the brain.
  After identifying the appropriate model, it is used to calculate the actual blood flow conditions, such as the blood flow velocity during a stroke. The formula for this calculation is: 
  
## Page 10 Intensity Temporal Autocorrelation Function

- 接下来介绍实验结果。
  这张图展示了相机捕获到在不同帧对应时间下的散斑强度在空间中的分布，从这张图中可以得到在不同区域中，散斑强度与时间的关系，也就是这张图展示的内容，然后可以将这些数据带入到这个公式中，便可得到不同区域中强度时间自相关函数与滞后时间的关系。
  可以看到时间强度自相关函数在静脉中的衰减速度最快，在实质组织中的衰减速度最慢，这是因为，血流越快，g2衰减越快，而静脉血流速度大于动脉大于实质组织。
  而这张图更直观地反映了这种关系，我们可以看到时间滞后值为440μs时，在静脉以及动脉血管中的g2值已经很小了，但实质组织中，仍有一部分的g2值很大。
- Next, let's discuss the experimental results.
  This image displays the distribution of speckle intensities captured by the camera at different frame times across spatial regions. From this image, we can derive the relationship between speckle intensity and time for different areas, which is the focus of this image. These data can then be input into the following formula to obtain the relationship between the intensity temporal autocorrelation function and the lag time for different regions:

  \[ g_2(\tau) = \frac{\langle I(t) I(t + \tau) \rangle}{\langle I(t) \rangle^2} \]

   It is observable that the decay rate of the intensity temporal autocorrelation function is fastest in veins and slowest in parenchymal tissues. This is because the faster the blood flow, the quicker the decay of \(g_2\), with venous blood flow being faster than arterial, which in turn is faster than that in parenchymal tissues.

  This graph more intuitively reflects this relationship; we can see that at a time lag of 440μs, the \(g_2\) values in the veins and arteries have significantly decreased, whereas in the parenchymal tissue, some \(g_2\) values remain relatively high. 
  
## Page 11 DLSI model fitting effects

- 这张图向我们展示了模型拟合的效果，我们在原理部分有讲到过，n描述不同的动态模式，n = 0.5对应MU，n = 1 对应MO/SU, n = 2 对应SO，
  图a展示了不同区域对应的最佳拟合模型的动态散射类型。
  图b展示了不同区域对应的最佳拟合模型的相关时间常数。
  图c展示了不同区域对应的最佳拟合模型的动态相干参数。
  这三张图展示了不同动态类型下，不同区域中的拟合优度。
  从这几张图中可以看到不同的动态模式比如MUn=0.5, SU/MOn=1, SOn=2适用于不同脑区和血管类型。动态模式与区域特性，例如血管大小、血流速度有关
  而这两张图展示了本文的优化模型与基础模型的拟合结果与真实实验数据的相似度，可以看到，在任何动态模式下，优化模型的拟合曲线都更接近真实数据。
- This figure demonstrates the effectiveness of model fitting, which was discussed in the principles section. The parameter \(n\) describes different dynamic modes, where \(n = 0.5\) corresponds to multiple unordered scattering (MU), \(n = 1\) corresponds to multiple ordered/single unordered scattering (MO/SU), and \(n = 2\) corresponds to single ordered scattering (SO). 
  - **Panel a** displays the dynamic scattering types that best fit different regions, showing the optimal fitting model for each area.
  - **Panel b** illustrates the correlation time constants for the best fitting models in different regions.
 - **Panel c** shows the dynamic coherence parameters for the best fitting models in different areas.
   These three panels together exhibit the goodness of fit across different regions under various dynamic types.
   From these figures, we can observe that different dynamic modes such as MUn=0.5, SU/MOn=1, SOn=2 are suitable for different brain areas and types of vessels. The dynamic modes correlate with regional characteristics, such as vessel size and blood flow velocity.
   The last two panels compare the fit results of the optimized model and the basic model with the actual experimental data, demonstrating that under any dynamic mode, the optimized model's fit curves are closer to the real data. 



## Page 12 Other Potential Uses

- 接下来展示一个DLSI的具体应用。
  这张图展示了DLSI在皮肤组织中的应用，
  图a显示皮肤组织内散斑强度的空间分布，高强度区域可能与皮肤血管或散射系数较高的组织有关，而低强度区域可能对应组织间隙或动态较低的区域。
  图b显示了皮肤组织中不同的动态模式，揭示了皮肤组织在不同区域内的动态特性。
- Next, let's look at a specific application of DLSI.
  This figure illustrates the use of DLSI in skin tissue:
  - **Panel a** displays the spatial distribution of speckle intensity within the skin tissue. Areas of high intensity may be associated with skin blood vessels or tissues with a higher scattering coefficient, while low-intensity areas might correspond to interstitial spaces or regions with lower dynamics.
  - **Panel b** shows different dynamic modes in the skin tissue, revealing the dynamic characteristics of the skin in various regions.
  This example demonstrates how DLSI can be effectively used to map and understand the complex structures and blood flow characteristics in skin, providing valuable insights that could be critical for dermatological studies or medical diagnostics.



## Page 13 Conclusion

- 最后就是总结了，包括DLSI的优势以及未来发展方向。
  DLSI有这几个优势。
  当然，DLSI也有一些未来的发展方向，比如改进硬件以提高帧速率；对模型进行优化，DLSI模型中对噪声贡献的简化表示是当前的一个局限，未来需要进一步研究量化高速CMOS传感器和光源不稳定性（如模式跳跃）产生的噪声及其对强度时间自相关函数的贡献，从而完善模型，提高测量和分析的准确性。
- Finally, let's summarize the advantages of Dynamic Light Scattering Imaging (DLSI) and its future development directions.
   DLSI has these advantages.
   Of course, there are some future directions for DLSI as well
   One of the future directions involves improving hardware to increase frame rates.
   Currently, the representation of noise contributions in the DLSI model is somewhat simplified. Future research needs to further explore and quantify the noise generated by high-speed CMOS sensors and instability in light sources, such as mode hopping. This research will help refine the model, enhancing the accuracy of measurements and analyses.
## Page 14 Thank you

  My presentation concludes here. Thank you, everyone, for your attention. Do you have any questions?
## Questions and answers
1. How does DLSI differ from LDF and  LSCI? (Yi Xiang)
Answer: DLSI combines high-speed imaging with advanced scattering models to directly measure the temporal autocorrelation function of speckle intensity, providing higher accuracy and adaptability to complex tissue environments, whereas LDF and LSCI typically offer only qualitative analysis of relative blood flow velocity or changes.
- 动态光散射成像（DLSI）与传统的激光多普勒流量计（LDF）和激光散斑对比成像（LSCI）有何不同？
答：DLSI结合了高速成像与先进的散射模型，能够直接测量散斑强度时间自相关函数，提供更高的精度和对复杂组织环境的适应性，而LDF和LSCI通常只能提供相对血流速度或血流变化的定性分析。

2. How does DLSI improve the precision of experimental data?
Answer: By capturing speckle images with high-speed CMOS cameras and incorporating complex data analysis models, DLSI can intricately parse the dynamics of blood flow and scattering mechanisms at a microscopic level, thus enhancing measurement precision.
- DLSI如何提高实验数据的精确性？
答：DLSI通过使用高速CMOS相机捕捉散斑图像，并结合复杂的数据分析模型，可以详细解析微观尺度上的血流动态和散射机制，从而提高测量的精确性。

3. What is the purpose of collimating and polarizing a laser? (Patricia Cui)
Answer: The laser is collimated to ensure that the laser shines uniformly on the animal tissue, and polarized to control the polarization state of the laser to reduce optical noise.
- 对激光进行准直和偏振的作用是什么？
答：对激光进行准直是为了确保激光能够均匀地照在动物组织上，偏振是为了控制激光的偏振态从而减少光学噪声

4. What is the process for analyzing and processing DLSI data? (Yulin Chen)
Answer: DLSI data analysis begins with image capture and preprocessing, followed by the application of complex algorithmic models to analyze the scattering images, and finally, statistical methods such as the F-test are used to verify the fit of the models and the reliability of the data.
- DLSI数据的分析处理流程是怎样的？
答：DLSI数据分析首先包括图像的采集与预处理，接着是应用复杂的算法模型对散射图像进行分析，最后利用统计方法如F检验来验证模型的拟合度和数据的可靠性。

