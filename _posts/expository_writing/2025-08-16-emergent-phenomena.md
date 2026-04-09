---
title: "Emergent Phenomena"
date: 2026-03-10w
pinned: true
---

**Ryder McDowell** · March 10, 2026 
---
<div style="background-color: #E4F2E1; padding: 10px; color: #1a1a1a;">
We thought building a bridge would be simple. We had all the necessary materials---sticks, palm fronds, dead branches---and a clear goal: cross the canal to the island on the other side. We piled everything into the water and waited for the structure to emerge. Instead, it all sank. One by one, the pieces disappeared into the dark brackish water, leaving no path forward. The ingredients were familiar. The outcome was not.
</div>


Condensed matter physics asks a similar question: what happens when you assemble many simple components? As Michael Levin put it, the field asks "what are all possible things that can happen if we put these particles together?"[^1] For a long time, we thought we had the clean-cut answer. Landau's theory of symmetry breaking classified phases of matter by identifying local order parameters that distinguished one state from another. If you knew the building blocks and their symmetries, you knew the phase. But we found certain materials evaded this description. They exhibited states whose defining features were not visible locally and not captured by symmetry alone. The framework, like our bridge, did not hold. Out of that failure emerged the idea of topological order---a recognition that matter can organize itself in ways our older theories did not anticipate.

<div style="background-color: #E4F2E1; padding: 10px; color: #1a1a1a;">

It's summer, early June, and my dad worked a half-day: the possibilities for discovery are limitless. I stand waiting for him between our wooden front door and plastic screen door. Below my bare feet, I glance down at the imprint of my own feet cast into the concrete when I was a baby. I'm anxious to go play in the woods while there's still daylight, and as soon as his truck pulls up I swing the screen door open, push off the step, and race up to the driver-side door. As soon as he says yes, I'm off. It's 96 degrees out and my feet burn on the concrete as I rush down the street to knock on doors and collect some other neighborhood kids to go with me.
</div>
The scientific version of this impulse led me to topological phases of matter.

---

## What are topological phases of matter?

You likely remember learning in an early science class that water can be a solid, liquid, or gas. The useful feature of those phases is that you can zoom in on a small region and tell, more or less immediately, what phase you are looking at based on how tightly packed the particles are and how they move. For a long time, physics assumed this local logic was general. Topological phases are one of the clearest examples that it is not.

In topological phases, the important information is not always visible in any small isolated patch. The difficulty is tied to a phenomenon in quantum mechanics known as entanglement.[^chen2010] Xie Chen, another leading researcher in this field, describes entangled particles as being "born that way, like twins."[^clavin2019] Even if they are separated, their properties remain deeply related. If a material is built from quantum particles with this kind of long-distance entanglement, then looking only at a small local section may no longer be enough to understand what phase the material is in.

That is what makes topological phases so strange and so interesting: some materials cannot be classified by anything purely local. Rather, their defining structure is global. This is the basic reason the field forced physicists to move beyond older classification schemes.[^wen2017] If ordinary phases are things we can diagnose up close, topological phases are phases whose identity is distributed across the whole system.

<div style="background-color: #E4F2E1; padding: 10px; color: #1a1a1a;">

<p> Recently, we'd been talking about going deeper into the woods than we ever had before. There wasn't a clear rule about how far back we could go, but we were explicitly banned from going into the marsh, so we knew we had to move quickly to avoid getting caught. After some careful deliberation we decided today was the perfect day for it and set out for greatness. It had rained hard that morning, which meant that about thirty feet into the woods, where the marsh leaked in at high tide, everything was still completely flooded. This meant we had to climb through the canopies of the trees to cross. The theatrics of this cost us about thirty minutes, but we safely crossed and kept trekking deeper.
</p>
<p>
Eventually, we found an opening into the marsh and stumbled onto an expansive sawgrass plain. The rain had made it particularly difficult to traverse, and all our slipping resulted in a lot of lashing from the sawgrass. It hurt, but this whole terrain was brand new to us, and we kept going even as the mud crept higher up our legs. Finally, we reached the edge of the plain, where the mud fully gave way to a canal about eight feet across. On the other side was a whole new piece of woods, mostly Florida pines and fewer big oak trees. As we stood there uncertainly discussing what to do next, I saw something rustling in the bushes on that island, and before I even saw anything emerge, I let out a shrill scream and sprinted away, leading our adventuring party straight home. </p>
</div>
---

## Landau Theory, or what we thought was out there

Formally, physical states are in the same phase of matter if one can be slowly changed into the other. Traditionally, we characterize different phases by measurable properties such as density or magnetization. The modern study of phase transitions is often associated with Landau-Ginzburg theory, which proposed that for a given system we can identify an *order parameter*: a measurement that captures the relevant symmetry of the system and changes sharply across a phase transition.[^landau1937]

### What do we mean by symmetry?

Symmetry is a concept that was introduced so early that it's deceptively intuitive for something so powerful. In school it usually appears as reflection symmetry: a shape can be folded across a line and will line up with itself. Rotational symmetry is similar: rotate a shape by some angle and it still looks the same.
<div style="display: flex; justify-content: center; gap: 10px;">
<img src="/assets/img/figure_1.png" alt="figure_1" width="500">
</div>
This also shows up constantly in physics. Atoms and molecules can have spatial symmetries; the ammonia molecule NH₃ is a standard example. Crystal lattices do too: a metal lattice may be preserved by reflections or rotations in much the same way a square on paper is.
<div style="display: flex; justify-content: center; gap: 10px;">
<img src="/assets/img/figure_2.jpg" alt="figure_2" width="220 "> <img src="/assets/img/figure_3.png" alt="figure_3" width="300">

</div>



In essence, when we say a physical system has a symmetry, we mean there is some transformation we can perform that leaves the system essentially unchanged.[^feynman1964]

Landau's framework used this idea beautifully. If two phases differ by symmetry, then an order parameter can distinguish them. In one phase the parameter is zero; in another it is nonzero.[^landau1937] This is why the framework is often described as a theory of symmetry breaking. Crucially, these were *local* order parameters.[^oxford_landau] As with water, you could zoom in on a small sample, make a local measurement, and correctly identify the phase.

![figure_4](/assets/img/figure_4.jpg)

This picture dominated for decades. It was powerful enough to classify crystal structures and explain a huge range of matter. Using this logic, physicists were able to organize the many possible crystal structures in three-dimensional space[^landau1937] and make sense of an enormous number of materials. But already, at the edges, there were hints that it was incomplete. Landau himself wrote that the behavior of Helium II "obviously cannot be explained by the classical theory" and was connected with quantum phenomena.[^landau1941] Something more complicated was lurking.

<div style="background-color: #E4F2E1; padding: 10px; color: #1a1a1a;">
<p>
Even after the hasty escape, the sawgrass cuts on my limbs, and the scolding for coming home with mud all the way up my legs, it had been worth it. My curiosity had been sparked. For a while it was all we talked about. Specifically, we came up with the idea to build a bridge to cross the canal. For a week, every day, we went out and collected sticks, dead branches, torn-down vines, and a truly unreasonable number of dead palm frond stalks and heads. We piled them near the beginning of the woods and one day set out to haul it all to the sawgrass plain.
</p>
<p>
Once we got there we had to carry everything to the edge of the canal, and even though I'd worn jeans that day, the sawgrass had grown and now cut up my arms. Finally, we'd successfully transported our building materials to the water and, without much more thought, started throwing them in.
</p>
<p>
 This turned out not to be a very good plan. Slowly, instead of a momentous bridge assembling in front of our eyes, our long and arduous process came to a bitter end as everything sank into the dark brackish water. A few particularly buoyant sticks remained in sight, but the rest stuck out at odd angles or disappeared completely. We stood at the edge of the canal with a sense of unease and disappointment. A large stack of palm frond heads we had planned to use as decoration sat without purpose beside us. We all looked at each other speechlessly, unsure of what to do next.
 </p>
</div>
We had all the building blocks, but the bridge did not emerge as expected.

---

## Emergence

One word you hear constantly when learning about topological phases is *emergence*: the process by which large-scale organized behavior arises from many simple local interactions. A familiar example is a crowded hallway splitting into two streams of traffic. Each person is only trying not to collide with the people nearby, but from those local decisions a stable pattern appears. Nature offers similar examples: ants building living bridges or slime mold tracing an efficient path between food sources.

<div style="display: flex; justify-content: center; gap: 10px;">
<img src="/assets/img/figure_5.png" alt="figure_5" width="220 "> <img src="/assets/img/figure_6.jpg" alt="figure_6" width="300">

</div>

Emergent behavior is beautiful partly because it is difficult to predict. If you know how many atoms are in a material and the mass of each, you can add them up and get the total mass. That is not emergence.[^mckenzie2023] But many collective properties cannot be so easily recovered directly from the individual pieces. This is one of the central challenges of condensed matter theory.

Topological order emerged from exactly this difficulty. It was, in part, born from our trouble understanding superconductivity, itself an emergent phenomenon. In a superconductor, none of the individual atoms are superconductors on their own. Yet, their collective state is.[^mckenzie2023] That is why discoveries in this area can be so surprising: the ingredients may be familiar, yet when assembled they produce behavior no one expected. In the words of Wen, "we cannot use the richness of the components to understand the richness of the materials."[^wen2017]

---

## From Landau to beyond Landau

The route beyond Landau ran through a set of surprises in condensed matter.

In 1986, superconductivity was discovered in ceramic cuprates at temperatures well above what anyone thought possible.[^aps1986] [^aps2007bcs] Within months, theorists proposed that these materials might be described by a *quantum spin liquid*,[^anderson1987] a new kind of state with no natural home in the Landau framework. Soon after, formal links were drawn[^kalmeyer1987] between these ideas and the Fractional Quantum Hall Effect,[^laughlin1983] another phenomenon already known to resist the old classification scheme.

In 1989, Xiao-Gang Wen published "Chiral spin states and superconductivity,"[^wen1989] and in 1990 he introduced the phrase *topological order*[^wen1990] more formally, providing a way to classify states of matter that could not be captured by symmetry breaking alone. The point was not just that Landau's theory had failed in one corner case, but rather, some phases of matter were organized by something categorically different from local symmetry breaking.

Then came an experimental reckoning. Some early results seemed to support the relevant chiral phases,[^lyons1990] but those signals were later traced to surface contamination[^lawrence1992] rather than genuine symmetry breaking. The conclusion was unavoidable: the particular chiral spin states under discussion did not describe the high-temperature superconductors after all. As Chen, Gu, and Wen would later put it, topological order had become a theory with no experimental realization.[^chen2010]
<div style="background-color: #E4F2E1; padding: 10px; color: #1a1a1a;">

The bridge had sunk.

<p>
"Maybe it will still work."
</p>
<p>"Could be gators in there."
</p>
<p>
"We already threw all those sticks and nothin' came jumping out."
</p>
<p> Without another word, one of my friends "crossed" our bridge, meaning he waded chest-deep through the water. I was completely surprised. We never went in the water like that, for fear of gators. Before I could say anything another kid crossed. I gave in and sat down on the bank.
</p>
<p>"Well, I don't get my shoes and socks wet."
</p>
<p>
 Like the rest, I waded across. Not even one gator ate me. My friends hauled me up from the mud and we stood laughing, excited out of our minds about what we had done. Our thick cotton jeans were soaking wet. It seemed we'd all discovered the bottom to be loose mud, since our jeans and the bottoms of our shirts were caked in gray-brown sludge. In this moment of triumph the sun was bright and the smell of mud and salt water filled the air. Then we heard rustling on the island with us and fell silent.
 </p>
</div>
---

## A very rich world, or what we didn't expect to find

In the words of Xiao-Gang Wen, "Our world is very rich."[^wen2019science] Some highlights of this richness include the existence of quasiparticles and the prospect of topological quantum computation.

### Quasiparticles

One of the surprises that condensed matter keeps offering is the existence of *quasiparticles*: emergent objects that arise from the complicated interactions of huge numbers of fundamental particles.[^lewton2021] They are not independent little things in the way an atom is. A quasiparticle exists only inside a medium, as part of a larger collective state.

<p align="center">
<img src="/assets/img/figure_7.png" alt="figure_7" width="600">
</p>


An instructive example of a quasiparticle comes from semiconductors---materials that are between conductors and insulators. When an electron is missing from the crystal structure of a semiconductor, that *electron hole* is a quasiparticle in that it has a charge (the opposite of an electron) and it can move around the material. Further, the balance between electrons and electron holes determines the type of semiconductor. This situation is a lot like a bubble in a liquid,[^weller1967] where the absence of the liquid in a small region behaves like a thing in its own right, which can move through the material. Then the difference between the different semiconductors is like the difference between something being flat or carbonated.

In topological phases, the relevant quasiparticles can be even stranger. They include *anyons*, excitations whose behavior is essential to how we classify topological order. In some systems, exchanging two anyons does not simply return the state to where it started up to a plus or minus sign, as it does for ordinary particles. Their behavior instead records something about the path of the exchange itself.

Understanding these excitations has become a major part of the field, and recent work has even suggested the existence of bound ensembles behaving as anyonic molecules.[^wilkinson2025]

### Topological Quantum Computation

The idea of quantum computation dates back to the late 70s.[^benioff1980] It was heavily popularized by Feynman,[^feynman1981simulating] who initially proposed it might be easier to simulate quantum behavior on quantum hardware. Where classical computers use bits (0's and 1's), a quantum computer uses a *qubit*, which can be 0 or 1 or, due to superposition, can be 0 and 1 at the same time.[^bitsvsqubits] Now we're firmly in the era of quantum computers and one of the most popular types of QC uses something called superconducting qubits. Yet, one problem we continue to face is dealing with errors in quantum computers. Currently, quantum computers have to be housed[^cryo] in these massive chandelier structures where the entire thing is cryogenically cooled since "at higher temperatures, qubits interact more with their environment, leading to errors in computations."[^postquantum_weird]


<p align="center">
<img src="/assets/img/figure_8.png" alt="figure_8" width="600">
</p>

In trying to understand what phases of matter are possible, we stumbled onto structures that happen to be technologically promising at dealing with these errors. In his seminal work, *Fault-tolerant quantum computation by anyons*, theorist Alexei Kitaev introduced the connection between topological order and quantum error correction.[^kitaev2003] The basic idea is that the long-range interactions associated with topological order make these systems resistant to errors from small local fluctuations (like heat). There has been genuine experimental progress[^satzinger2021] in recent years, along with familiar controversy and skepticism. Claims involving topological qubits, Majorana devices, moiré materials, and topological superconductors have generated both excitement and pushback. That pattern feels appropriate for this subject. The field keeps discovering that the world is stranger than expected, but it rarely yields its secrets quickly.

<div style="background-color: #E4F2E1; padding: 10px; color: #1a1a1a;">

<p> Suddenly, everything was very still. It turns out that the scary part about getting onto an island in the marsh is that somehow, suddenly, you are on an island in the marsh. Also, in some particularly unfortunate cases, you are seven years old. The humid air hung oppressively over us while the sun baked. It was too early for cicadas. There was nothing. </p>
<p>
Again, we heard the rustling and finally turned to locate the source of the noise. We looked down the long corridor of open land on the island. The tall Florida pines cast cascading prison-bar shadows across the ground.
</p>
At the opposite end of this corridor stood a family of deer. Maybe several families of deer. We stood stunned by their presence, only able to stare in awe at them. They looked back at us plainly. Just as still. Just as silent.
<p>
 I don't know how long the moment lasted. On my end it is completely stationary. I had never seen that many deer at once before, and I never did again. But I can still feel that enveloping sense of pure awe.
</p>
<p>
 Our discovery had been made and our curiosity, for the moment, was satisfied. We finally went home that day and never revisited the island.
 </p>
</div>
---

I think that is still what draws me to condensed matter theory. Not only the possibility of usefulness or the hope that topological phases may reshape quantum technologies. It is also the chance to discover that the world is structured in ways we did not expect; that even when our old frameworks fail, there is still something there to find. We cross, we sink the bridge, we wade through anyway, and sometimes on the other side there are deer.

But somehow always knowing that our world is very rich.

---

## Notes

[^1]: [Breakthrough Prize Laureate Quote Video](https://www.facebook.com/watch/?v=596122164332536)
[^cryo]: Not all quantum computers rely on cryogenics, but ones using superconducting qubits do.

## References

[^chen2010]: X. Chen, Z.-C. Gu, and X.-G. Wen, "Local unitary transformation, long-range quantum entanglement, wave function renormalization, and topological order," *Phys. Rev. B* **82**, 155138 (2010).
[^clavin2019]: W. Clavin, Caltech News, 2019.
[^wen2017]: X.-G. Wen, "Colloquium: Zoo of quantum-topological phases of matter," *Rev. Mod. Phys.* **89**, 041004 (2017).
[^landau1937]: L. D. Landau, "On the theory of phase transitions," *Zh. Eksp. Teor. Fiz.* **7**, 19 (1937).
[^feynman1964]: R. P. Feynman, *The Feynman Lectures on Physics*, Vol. 1 (1964).
[^oxford_landau]: Oxford Reference, "Landau–Ginzburg theory."
[^landau1941]: L. D. Landau, "Theory of the superfluidity of helium II," *Phys. Rev.* **60**, 356 (1941).
[^mckenzie2023]: R. H. McKenzie, *A Physicist's Introduction to Topology* (2023).
[^aps1986]: APS Physics, "The Discovery of High-Temperature Superconductors," 1986.
[^aps2007bcs]: APS Physics, "BCS Theory of Superconductivity," 2007.
[^anderson1987]: P. W. Anderson, "The Resonating Valence Bond State in La₂CuO₄ and Superconductivity," *Science* **235**, 1196 (1987).
[^kalmeyer1987]: V. Kalmeyer and R. B. Laughlin, "Equivalence of the resonating-valence-bond and fractional quantum Hall states," *Phys. Rev. Lett.* **59**, 2095 (1987).
[^laughlin1983]: R. B. Laughlin, "Anomalous quantum Hall effect," *Phys. Rev. Lett.* **50**, 1395 (1983).
[^wen1989]: X.-G. Wen, F. Wilczek, and A. Zee, "Chiral spin states and superconductivity," *Phys. Rev. B* **39**, 11413 (1989).
[^wen1990]: X.-G. Wen, "Topological orders in rigid states," *Int. J. Mod. Phys. B* **4**, 239 (1990).
[^lyons1990]: K. B. Lyons et al., *Phys. Rev. Lett.* **64**, 2949 (1990).
[^lawrence1992]: J. M. Lawrence et al., *Phys. Rev. B* **45**, 2515 (1992).
[^wen2019science]: X.-G. Wen, "Zoo of quantum-topological phases of matter," *Science* (2019).
[^lewton2021]: T. Lewton, "Quasiparticles," *Quanta Magazine* (2021).
[^weller1967]: P. F. Weller, "An Analogy for Elementary Band Theory Concepts in Solids," *J. Chem. Ed.* **44**, 391 (1967).
[^wilkinson2025]: S. Wilkinson et al., "Anyonic molecules," (2025).
[^benioff1980]: P. Benioff, "The computer as a physical system," *J. Stat. Phys.* **22**, 563 (1980).
[^feynman1981simulating]: R. P. Feynman, "Simulating physics with computers," *Int. J. Theor. Phys.* **21**, 467 (1982).
[^bitsvsqubits]: IBM Quantum, "Bits vs. Qubits."
[^postquantum_weird]: PostQuantum, "How quantum computers work."
[^kitaev2003]: A. Kitaev, "Fault-tolerant quantum computation by anyons," *Ann. Phys.* **303**, 2 (2003).
[^satzinger2021]: K. J. Satzinger et al., "Realizing topologically ordered states on a quantum processor," *Science* **374**, 1237 (2021).
[^vanbelle2015]: G. Van Belle, NH₃ symmetry diagram (2015).
[^tecscience2018]: TecScience, "Metallic Lattice" (2018).
