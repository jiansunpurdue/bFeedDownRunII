
<h1> bFeedDownRunII </h1>
<p> bFeedDownRunII is created to extract D0 prompt fractions. </p>

<h2> analysis/ </h2>
<h3> Introduction </h3>
<p> analysis/ is main anaysis macros. For each collision system, there are two steps: </p>
<ol>
<li> <code>analysis/*/savehist/project*.C</code>: Project and save histograms </li>
<li> <code>analysis/bFeedDownFraction.C</code>: Fit DCA distributions </li>
</ol>
<h3> How to run </h3>
<ul>
<li> Run all three collision systems (PP,PbPbcent0100,PbPbcent010) <br />
<code>
cd analysis/ <br />
source doall.sh 1 1
</code> <br />
<p> where the arguments decide whether to run each step. </p>
</li>
<li> Run one collision system (e.g. PP) <br />
<code>
cd analysis/PP/ <br />
source dobFeedDown.sh 1 1
</code> <br />
<p> where the arguments decide whether to run each step. </p> 
</li>
</ul>

<h2> pfFONLL/ </h2>
<h3> Introduction </h3>
<p> pfFONLL/ calculates and plots prompt fractions by FONLL. There are three steps: </p>
<ol>
<li> <code>pfFONLL/fonllDsigmadpt.C</code>: Calculate FONLL pp cross-sections </li>
<li> <code>MCefficiency.C</code><code>plotPnNP.C</code>: Calculate and MC efficiency </li>
<li> <code>fitBoverD.C</code><code>bFeedDownFONLL.C</code><code>plotFractions.C</code>: Set BRAA/DRAA ratios, calculate and plot prompt fractions </li>
</ol>
<h3> How to run it </h3>
<ul>
<li> Run all three collision systems <br />
<code>
cd pfFONLL/ <br />
source doall.sh 1 1 1
</code> <br />
<p> where the arguments decide whether to run each step. </p>
</li>
<li> Run one collision system <br />
<code>
cd pfFONLL/ <br />
source dobFeedDownFONLL.sh [c] 1 1 1
</code> <br />
<p> where <code>[c]</code> decides the system (0:PP, 1:PbPbcent0100, 2:PbPbcent010), and the others decide whether to run each step. </p>
</li>
</ul>

## finalPlots/
### Introduction
finalPlots/ plots the final plots comparing prompt fractions by DCA fitting and FONLL. There is one step:
<ol>
<li> <code>finalPlots.C</code> </li>
</ol>
It prerequires the results from <code>analysis/</code> and <code>pfFONLL/</code>. 
### How to run it
<ul>
<li> Run all three collision systems 
<code>
cd finalPlots/
source doall.sh
</code>
</li>
<li> Run one collision system
<code>
cd finalPlots/
source dofinalPlots.sh [c]
</code>
<code>[c]</code> decides the system (0:PP, 1:PbPbcent0100, 2:PbPbcent010).
</li>
</ul>

## MCclosure/
### Introduction
MCclosure/ tests closure of the machinery. There are three steps:
<ol>
<li> <code>analysis/*</code>: Calculate the prompt fractions from DCA fitting machinery </li>
<li> <code>trueFprompt.cc</code>: Count the true prompt fractions from fake data </li>
<li> <code>compare.cc</code>:  Plot the comparison of prompt fractions from DCA fitting and true values </li>
</ol>
### How to run it
<code>
cd MCclosure/analysis/
source doall.sh 1 1
cd ..
source doMCclosure.sh 1 1
</code>

