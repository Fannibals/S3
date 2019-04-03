####Lecture 3 CCC

---

**1. Computer Scaling**

+ Vertical Computational Scaling
  + have faster processors
    + \+ easy to do, 
    + \- but costs more
  + limits of fundamental physics/matter
+ Horizontal Computational Scaling
  + Have more processors
    + \+ easy to add more, cost increase not that much
    + \- but harder to design, develop, test and etc

**2. MAKE FASTER - ADD MORE**

+ Single machine ***multiple cores***
  + more cores
+ **<font color=blue>Loosely</font>** **coupled cluster** of machines
  + pooling/sharing of resources
+ **<font color=blue>Tightly</font>** coupled cluster of machines

+ Widely distributed clusters of machines
+ Hybrid combinations of the above



**3. Limitation of ADD-MORE**

+ T(1) = time for serial computation
+ T(N) = time for N parallel computations
+ S(N) = speed up 

$$
\begin{align*}
S(N) = \frac{T(1)}{T(N)}
\end{align*}
$$



+ **Amdahl's Law**

  + $T(1) = \alpha + \pi$
    + alpha here means the serial part
    + pi here means the parallel part

  + $T(N) = \alpha + \frac{\pi}{N}$
  + $S \approx \frac{1}{\alpha}$
  + ***It also assumes a <font color=red>fixed problem size</font>*** 

+ **Gustafson-Barsis's Law**

  + didn't assume the problem is in a fixed size
  + <a href = "https://blog.csdn.net/qq_34594236/article/details/79674204">comparison</a>



**4. Computer Architecture**

+ At the simplest level a computer comprises:

  + CPU for excuting programs
  + Memory that stores/executing programs and related data
  + I/O systems
  + Design ---

+ **Flynn's Taxonomys**

  <table style = "width:85%">
      <tr>
          <th></th>
          <th>Single Instruction</th>
          <th>Multiple Instruction</th>
      </tr>
      <tr>
          <td><b>Single data</b></td>
          <td>SISD</td>
          <td>MISD</td>
      </tr>
      <tr>
          <td><b>Multiple data</b></td>
          <td>SIMD</td>
          <td>MIMD</td>
      </tr>
          <tr>
  </table>

  

**5. Approaches for Parallelism**

+ **Explicit vs. Implicit parallelism**
+ **Hardware**
  + Basic CPU
  + Hardware Threading CPU
  + Multi-Core 
  + **Symmetric Multiprocessing (SMP)**
  + **Non-Uniform Memory Access (NUMA)**
    + provdies speed-up by allowing a processor to access its own local memory faster than non-local memory.

+ **OS**
+ **Software Parallelism Approaches**
  + many languages can do that !
  + deadlock and livelock are key issues that need to be tackled



#### Message Passing Interface (MPI)

---

+ **Key MPI functions**
  + MPI_Init
  + MPI_Finalize
  + MPI_COMM_SIZE
  + MPI_COMM_RANK
  + MPI_SEND
  + MPI_RECV

+ Condor is another way using multiple cores



#### Data Parallelism Approaches

---

+ Challenges with Distribution
+ **<font color=red>Erroneous Assumptions of Distributed Systems</font>**
  + The network is reliable
  + Latency is zero
  + Bandwidth is infinite
  + The network is secure
  + Topology doesn't change
  + There is one administrator
  + Transport cost is zero
  + The network is homogeneous
  + Time is ubiquitous



#### Strategies for Development of Parallel/Distributed Systems

+ Design Stages of Parallel Programs
  + Partitioning 
  + Communication
  + Agglomeration
  + Mapping / Scheduling

+ Master - Slave Model