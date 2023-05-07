Download Link: https://assignmentchef.com/product/solved-m232-homework-9-numerical-analysis-ii
<br>
Consider the Lax-Wendroff method

In Matlab, we might be tempted to implement this method with periodic boundary conditions on the grid <em>x<sub>i </sub></em>= <em>ih </em>for <em>i </em>= 1<em>,</em>2<em>,</em>··· <em>,m </em>+ 1 with <em>h </em>= (<em>b </em>− <em>a</em>)<em>/</em>(<em>m </em>+ 1) within a time-stepping loop as

U(1) = U(1) − 0<em>.</em>5 ∗ nu ∗ (U(2) − U(m + 1))<em>…</em>

+0<em>.</em>5 ∗ nu^2 ∗ (U(m + 1) − 2<em>.</em>0 ∗ U(1) + U(2));

U(2 : m) = U(2 : m) − 0<em>.</em>5 ∗ nu ∗ (U(3 : m + 1) − U(1 : m − 1))<em>…</em>

+0<em>.</em>5 ∗ nu^2 ∗ (U(1 : m − 1) − 2<em>.</em>0 ∗ U(2 : m) + U(3 : m + 1));

U(m + 1) = U(m + 1) − 0<em>.</em>5 ∗ nu ∗ (U(1) − U(m))<em>…</em>

+0<em>.</em>5 ∗ nu^2 ∗ (U(m) − 2<em>.</em>0 ∗ U(m + 1) + U(1));

Note that periodic boundary conditions mean that <em>U</em><sub>0 </sub>= <em>U<sub>m</sub></em><sub>+1</sub>, so we do not solve for <em>U</em><sub>0 </sub>in the equations above. However, this implementation is incorrect. Can you find the bug?

<ol start="2">

 <li>Consider the numerical scheme:

  <ul>

   <li>With which system of PDEs is this scheme consistent?</li>

  </ul></li>

</ol>




<ul>

 <li>Find the modified equations for this scheme.</li>

 <li>Using von Neumann stability analysis find conditions on <em>k </em>and <em>h </em>sufficient for this scheme to be stable.</li>

</ul>

<ol start="3">

 <li>The m-file advection LW pbc.m implements the Lax-Wendroff method for the advection equation on 0 ≤ <em>x </em>≤ 1 with periodic boundary conditions.

  <ul>

   <li>Observe how this method behaves with <em>m </em>+ 1 = 50<em>,</em>100<em>,</em>200 grid points. Change the final time to tfinal = 0.1 and use the m-files error table.m and error loglog.m to verify second order accuracy.</li>

   <li>Modify the m-file to create a version advection up pbc.m implementing the upwind method and verify that this is first order accurate.</li>

   <li>Keep <em>m </em>fixed and observe what happens with advection up pbc.m if the time step <em>k </em>is reduced, e.g. try <em>k </em>= 0<em>.</em>4<em>h</em>, <em>k </em>= 0<em>.</em>2<em>h </em>and <em>k </em>= 0<em>.</em>1<em>h</em>. When a convergent method is applied to an ODE we expect better accuracy as the time step is reduced and we can view the upwind method as an ODE solver applied to a Method of Lines system. However, you should observe decreased accuracy as <em>k </em>→ 0 with <em>h </em> Explain this apparent paradox. (Hint: What ODE system are we solving with more accuracy? You might also consider the modified equation given by (10.44) in LeVeque).</li>

  </ul></li>

</ol>

2