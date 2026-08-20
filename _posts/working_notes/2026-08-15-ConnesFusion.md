---
layout: post
title:  Connes Fusion
date:   2026-08-15 22:57:49 +0000
categories: jekyll update
usemathjax: true
---
<style>
.note { position: relative; }

.note-toggle {
  position: absolute !important;
  opacity: 0 !important;
  width: 0 !important;
  height: 0 !important;
  margin: 0 !important;
  padding: 0 !important;
  border: 0 !important;
  appearance: none !important;
  -webkit-appearance: none !important;
  pointer-events: none !important;
}

.note-ref {
  display: inline-block;
  vertical-align: super;
  font-size: 0.7em;
  font-weight: 600;
  line-height: 1;
  padding: 0.2em 0.45em;
  margin: 0 0.12em;
  border-radius: 0.6em;
  background: rgba(128, 128, 128, 0.22);
  color: #7aa2d6;
  cursor: pointer;
  user-select: none;
  transition: background 0.15s ease, color 0.15s ease;
}
.note-ref::before {
  counter-increment: note;
  content: counter(note);
}
.note-ref:hover { background: rgba(128, 128, 128, 0.38); }
.note-toggle:checked ~ .note-ref { background: #7aa2d6; color: #14161a; }

.note-body {
  position: absolute !important;
  z-index: 60;
  left: 0;
  top: 1.9em;
  width: min(32rem, calc(100vw - 2.5rem));
  padding: 0.85rem 1rem;
  font-size: 0.88rem;
  font-weight: 400;
  font-style: normal;
  line-height: 1.5;
  text-align: left;
  text-indent: 0;
  background: #21242a;
  color: #d7dae0;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 6px;
  box-shadow: 0 8px 28px rgba(0, 0, 0, 0.55);
  opacity: 0 !important;
  visibility: hidden !important;
  transform: translateY(-4px);
  transition: opacity 0.15s ease, transform 0.15s ease, visibility 0.15s;
}
.note-body::before {
  content: counter(note) ".";
  font-weight: 700;
  margin-right: 0.4em;
  color: #7aa2d6;
}
.note-toggle:checked ~ .note-body {
  opacity: 1 !important;
  visibility: visible !important;
  transform: none;
}

@media print {
  .note-body {
    position: static !important;
    display: block;
    opacity: 1 !important;
    visibility: visible !important;
    transform: none;
    width: auto;
    background: none;
    color: inherit;
    border: 0;
    border-left: 3px solid #999;
    box-shadow: none;
    margin: 0.5rem 0;
  }
}
</style>

<script>
(function () {
  var root = document.body || document.documentElement;
  root.style.counterReset = 'note';

  if (!window.MathJax) {
    window.MathJax = {
      tex: {
        inlineMath: [['\\(', '\\)']],
        displayMath: [['\\[', '\\]'], ['$$', '$$']],
        tags: 'none'
      },
      options: {
        skipHtmlTags: ['script', 'noscript', 'style', 'textarea', 'pre', 'code']
      }
    };
    var mj = document.createElement('script');
    mj.src = 'https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js';
    mj.async = true;
    document.head.appendChild(mj);
  }

  document.addEventListener('change', function (e) {
    var box = e.target;
    if (!box.classList || !box.classList.contains('note-toggle')) return;
    if (!box.checked) return;
    var all = document.querySelectorAll('.note-toggle:checked');
    for (var i = 0; i < all.length; i++) {
      if (all[i] !== box) all[i].checked = false;
    }
    nudge(box.parentNode.querySelector('.note-body'));
  });

  document.addEventListener('click', function (e) {
    if (e.target.closest && e.target.closest('.note')) return;
    closeAll();
  });
  document.addEventListener('keydown', function (e) {
    if (e.key === 'Escape') closeAll();
  });

  function closeAll() {
    var open = document.querySelectorAll('.note-toggle:checked');
    for (var i = 0; i < open.length; i++) open[i].checked = false;
  }

  function nudge(body) {
    if (!body) return;
    body.style.left = '0px';
    var rect = body.getBoundingClientRect();
    var over = rect.right - (window.innerWidth - 12);
    if (over > 0) body.style.left = -over + 'px';
    if (rect.left < 12) body.style.left = (12 - rect.left) + 'px';
  }
})();
</script>

Following Chapter 3 of [Unitary Quantum Symmetries Lite](https://people.math.osu.edu/penneys.2/UQSL/UQSL.html) from Penneys, Ferrer, and Kawagoe we want to try to first establish what Connes fusion is. Big picture: just like when we compose (fuse) group representations on Hilbert spaces, we end up in the tensor product Hilbert space; Connes fusion is the equivalent for modules over an algebra.  

This text gives three equivalent definitions. For now let's restrict ourselves to the first one.

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a;">
<b style="color: #1a1a1a;">Definition: Connes Fusion.</b>
<br>
Given a right B-module \(H_B\) and a left B-module \({}_{B}K\). We define the <b style="color: #1a1a1a;">Connes Fusion</b> relative tensor product Hilbert space \(H\boxtimes_B K\) can be defined using the relative tensor product for \(C^*\)-Hilbert modules.

$$ Hom(L^2B_B \rightarrow H_B) \boxtimes_B K$$
with \(\mathbb{C}\)-valued inner product

$$\langle f_1 \boxtimes \eta_1 \vert f_2 \boxtimes \eta_2 \rangle := \langle \langle f_2 \vert f_1 \rangle_B \eta_1 \vert \eta_2 \rangle_K$$
where we have
$$\langle f_2 \vert f_1 \rangle_B = f_2^{\dagger}f1 \in End(L^2B_B)=B$$
</div>

We aim to build up the tools to understand this definition within this post.

### Modules

In general, modules can be thought of as a generalazition of a vector space, where we let the scalars come from a ring rather than a field. However, what we're really interested in is modules of algebras. Translating to that language we have:

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">

<b style="color: #1a1a1a;">Definition — Left Module.</b> <br>
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #008000;">VecSpace</span><span style="color: #1a1a1a;">, </span><span style="color: #0000FF;">BilinearMap</span><span style="color: #1a1a1a;">)</span></span>

Suppose \(A\) is a unital algebra. A (left) module \({}_{A}M\) for \(A\) is a vector space \(M\) equipped with a bilinear map \( \triangleright: A \times M \rightarrow M \) satisfying:
<br>
1. (associativity) $$a \triangleright (b \triangleright m) = (a \cdot b) \triangleright m \text{ for } m \in M \text{ and } a,b \in A$$
2. (unitality) $$1 \triangleright m = m \text{ for } m \in M$$
</div>

<!-- commentary -->

<hr style="border: none; border-top: 1px solid black;">
<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">

<b style="color: #1a1a1a;">Definition — Right Module.</b> <br>
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #008000;">VecSpace</span><span style="color: #1a1a1a;">, </span><span style="color: #0000FF;">BilinearMap</span><span style="color: #1a1a1a;">)</span></span>
Suppose \(A\) is a unital algebra. A (right) module \(M_A\) for \(A\) is a vector space \(M\) equipped with a bilinear map \( \triangleleft: M \times A \rightarrow M \) satisfying:
<br>
1. (associativity) $$(m \triangleleft a) \triangleleft b = m \triangleleft (a \cdot b) \text{ for } m \in M \text{ and } a,b \in A$$
2. (unitality) $$m \triangleleft 1 = m \text{ for } m \in M$$
</div>

Using these let's understand the definition of a bimodule over two algebras.

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #008000;">VecSpace</span><span style="color: #1a1a1a;">, </span><span style="color: #0000FF;">UnitalMap</span><span style="color: #1a1a1a;">)</span></span>
<b style="color: #1a1a1a;">Definition: A–B Bimodule.</b> <br>
An A–B bimodule \(M\), denoted \({}_{A}M_{B}\) is a right B-module, \(M_B\) equipped with a unital algebra map \( \cdot: A  \rightarrow End(M_B)\)
</div>

### The Algebraic Relative Tensor Product

<par>
For modules of an algebra, \(\mathcal{A}, M_A, {}_{A}N\), the relative tensor product \(M \otimes_A N \) is the quotient of the tensor product \( M \otimes N \) subspace generated by

$$ K =  \{ ma \otimes n - m \otimes an \; \vert \; m \in M, a\in \mathcal{A},  \text{ and } n \in N \} \subset M \otimes N$$

In short, \( M \otimes_A N = M \otimes N / K\). Hence, \(ma \otimes_A n = m \otimes_A an\).

This gives a sense of what the relative tensor product is supposed to accomplish, but to properly understand Connes fusion, we need to understand the relative tensor product of Hilbert bimodules, for which we have to understand the role of the inner product in this discussion. 

</par>

<!-- commentary -->

### Algebra-Valued Inner Products & Hilbert C*-Modules

<!-- commentary: motivate why the plain quotient above isn't enough — a correspondence needs geometry, i.e. an algebra-valued inner product -->

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #0000FF;">InnerProduct</span><span style="color: #1a1a1a;">)</span></span>
<b style="color: #1a1a1a;">Definition: A-valued Inner Product.</b> <br>
Suppose \(X_A\) is a right module for a unitary algebra \(A\). An <b style="color: #1a1a1a;">\(A\)-valued inner product</b> is a map \(\langle \cdot \vert \cdot \rangle_A : X \times X \rightarrow A\) satisfying:
<br>
1. (\(A\)-linear in the second variable) $$\langle \varphi \vert \zeta_1 a + \zeta_2 \rangle_A = \langle \varphi \vert \zeta_1 \rangle_A \, a + \langle \varphi \vert \zeta_2 \rangle_A$$
2. (conjugate-symmetric) $$\langle \varphi \vert \zeta \rangle_A^{*} = \langle \zeta \vert \varphi \rangle_A$$
3. (positive-definite) $$\langle \varphi \vert \varphi \rangle_A \geq 0 \text{ in } A, \text{ with equality iff } \varphi = 0.$$
</div>
<par>
We note here that every unital algebra, \(\mathcal{A}\), has the trivial \(\mathcal{A}\)-valued inner product
$$ \langle a \; \vert \; b \rangle_A := a^*b $$
</par>

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #8502c7;">Module</span><span style="color: #1a1a1a;">, </span><span style="color: #0000FF;">InnerProduct</span><span style="color: #1a1a1a;">)</span></span>
<b style="color: #1a1a1a;">Definition: Right Hilbert C*-Module.</b> <br>
A right module equipped with an C* algebra valued inner product is a <b style="color: #1a1a1a;">right Hilbert \(C^*\)-module</b>.
</div>
<par>
So at this point it seems like we're pretty close to fusion with an inner product. Let's take a left and right Hilbert C*-module over B and consider the relative tensor product from above
$$M \otimes_B N = (M \otimes N) / \{ mb \otimes n - m \otimes bn \} $$
Recall that by definition we know that \(M_B\) and \({}_{B}N\) are equipped with B-valued inner products. Hence, in the tensor product space \(M \otimes_B N\) we might hope to define
$$ \forall m_1,m_2 \in M, \; n_1, n_2 \in N \qquad  \langle m_1 \otimes n_1 \; \vert \; m_2 \otimes n_2 \rangle_{\mathbb{C}} := {}_{\small{B}}\langle n_1 \vert \; \langle m_1 \vert m_2 \rangle_{\small{B}} \, n_2\rangle$$
but this is only a well-defined function on \(M \otimes_B N\) if it respects the quotient relation \(mb \otimes n = m \otimes bn\).

Here if we replace \(m_1\) with \(m_1 b\) on the left slot:
$$\langle m_1 b \otimes n_1 \; \vert \; m_2 \otimes n_2\rangle_{\mathbb{C}} = {}_{\small{B}}\langle n_1 \; \vert \; \langle m_1 b \vert m_2\rangle_{\small{B}} \, n_2\rangle = {}_{\small{B}}\langle n_1 \; \vert \; b^* \langle m_1 \vert m_2\rangle_{\small{B}}  n_2\rangle$$
using the property<span class="note"><input type="checkbox" id="note-2" class="note-toggle"><label for="note-2" class="note-ref"></label><span class="note-body">By conjugate-symmetry, \(\langle mb \vert m'\rangle_B = \langle m' \vert mb\rangle_B^{*}\). By B-linearity in the second slot, \(\langle m' \vert mb\rangle_B = \langle m' \vert m\rangle_B \, b\). Taking the adjoint: \(\big(\langle m' \vert m\rangle_B \, b\big)^{*} = b^{*} \langle m' \vert m\rangle_B^{*} = b^{*} \langle m \vert m'\rangle_B\). So \(\langle mb \vert m'\rangle_B = b^{*} \langle m \vert m'\rangle_B\) .</span></span> 
\(\langle mb \vert m'\rangle_B = b^* \langle m \vert m'\rangle_B\) of a right B-valued inner product.

Replacing \(n_1\) with \(bn_1\) on the right slot instead:
$$\langle m_1 \otimes bn_1 \; \vert \; m_2 \otimes n_2\rangle_{\mathbb{C}} = {}_{\small{B}}\langle bn_1 \; \vert \; \langle m_1 \vert m_2\rangle_{\small{B}} \, n_2\rangle$$
For the two expressions to agree, we need
$${}_{\small{B}}\langle n_1 \; \vert \; b^* \langle m_1 \vert m_2\rangle_{\small{B}} \, n_2\rangle = {}_{\small{B}}\langle bn_1 \; \vert \; \langle m_1 \vert m_2\rangle_{\small{B}} \, n_2\rangle$$
Writing \(\eta := \langle m_1 \vert m_2 \rangle_{\small{B}} \, n_2 \in N\), this must hold for every \(m_1, m_2\) — but as \(m_1, m_2\) range over \(M\), the element \(\langle m_1 \vert m_2 \rangle_{\small{B}}\) ranges over all of \(B\) and \(n_2\) is arbitrary, so \(\eta\) ranges over all of \(N\). The condition therefore reduces to
$${}_{\small{B}}\langle n_1 \; \vert \; b^* \eta\rangle = {}_{\small{B}}\langle bn_1 \; \vert \; \eta\rangle \qquad \forall b \in B, \; n_1, \eta \in N.$$
Thus left B-action on N consists of operators that admit adjoints with respect to \({}_{B}\langle \cdot, \cdot \rangle\) where the adjoint of acting by \(b\)  is just acting by \(b^*\).
</par>
<br>
<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold; color: #787879;">Condition</span>
<b style="color: #1a1a1a;">Definition: Adjointable Operator.</b> <br>
Suppose \(X_A, Y_A\) are right modules equipped with \(A\)-valued inner products. A right \(A\)-linear map \(x : X \rightarrow Y\) is <b style="color: #1a1a1a;">adjointable</b> if there is a right \(A\)-linear map \(x^{\dagger} : Y \rightarrow X\), called an <b style="color: #1a1a1a;">adjoint</b>, such that
<br>
$$\langle x^{\dagger}\varphi \vert \zeta \rangle_A = \langle \varphi \vert x\zeta \rangle_A \qquad \forall \zeta \in X, \; \varphi \in Y$$
where the left inner product is on \(X\) and the right one is on \(Y\).  
</div>
<hr style="border: none; border-top: 1px solid black;">


<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #008000;">VecSpace</span><span style="color: #1a1a1a;">, </span><span style="color: #0000FF;">InnerProduct</span><span style="color: #1a1a1a;">)</span></span>
<b style="color: #1a1a1a;">Trick: Realization (Self-Enrichment).</b> <br>
For any right Hilbert \(C^*\)-module \(X_A\), the adjointable maps \(AdHom(A_A \rightarrow X_A)\) themselves form a right Hilbert \(C^*\)-module with \(A\)-valued inner product
<br>
$$\langle f \vert g \rangle_A := f^{\dagger} \circ g \in End(A_A) = A$$
<br>
<div style="background-color: #f9f1f1; padding: 10px; color: #1a1a1a; position: relative; border: 1px solid black;">
<u><b style="color: #1a1a1a;">Pf.</b> </u>
<par>
We want to show that \(\mathcal{H} := AdHom(A_A \rightarrow X_A)\), the set of adjointable<span class="note"><input type="checkbox" id="note-3" class="note-toggle"><label for="note-3" class="note-ref"></label><span class="note-body">We take the \(\dagger\) operation on one of these maps to denote it's adjoint i.e. \( f \in AdHom(A_A, X_A) \implies f^{\dagger}  \in Ad(Hom(X_A,A_A) \)</span></span>  right A-linear maps \(A_A \rightarrow X_A\), is a right Hilbert \(C^*\)-module. We'll do this in three steps: first show \(\mathcal{H}\) is a vector space, then equip it with a right A-action, and finally define the A-valued inner product.
</par>
<br>
<par>
<b style="color: #1a1a1a;">Step 1: \(\mathcal{H}\) is a vector space.</b> 
Define \((f + g)(a) := f(a) + g(a)\) and \((\lambda f)(a) := \lambda f(a)\) for \(\lambda \in \mathbb{C}\). These preserve right A-linearity, since
\[(f+g)(a \cdot b) = f(a) \cdot b + g(a) \cdot b = (f+g)(a) \cdot b\]
and preserve adjointability, since \((f+g)^{\dagger} = f^{\dagger} + g^{\dagger}\) and \((\lambda f)^{\dagger} = \bar{\lambda} f^{\dagger}\)
</par>
<br>
<hr style="border: none; border-top: 1px solid black;">
<par>
<b style="color: #1a1a1a;">Step 2: \( \mathcal{H} \) is a right A-module. </b> 
Define \(\triangleleft : \mathcal{H} \times A \rightarrow \mathcal{H}\) by
\[(f \triangleleft a)(b) := f(a \cdot b)\]
We verify: (a) \(f \triangleleft a \in \mathcal{H}\), (b) \(\triangleleft\) is bilinear, and (c) \(\triangleleft\) is associative and unital.
</par>
<br>
<par>
<b style="color: #1a1a1a;"> (a) \(f \triangleleft a \in \mathcal{H}.\) </b>
<br>
<u> Right A-linear:</u>
\[(f \triangleleft a)(b \cdot c) = f(a \cdot b \cdot c) = f(a \cdot b) \cdot c = (f \triangleleft a)(b) \cdot c\]
<u> Adjointable: </u> <br>
Define \(g : X \rightarrow A\) by \(g(\xi) := a^* \cdot f^{\dagger}(\xi)\). This is right A-linear, and satisfies
\[\begin{aligned}
\langle g(\xi) \vert b\rangle_A &= \langle a^* f^{\dagger}(\xi) \vert b\rangle_A \\
&= (a^* f^{\dagger}(\xi))^* b \\
&= f^{\dagger}(\xi)^* a b \\
&= \langle f^{\dagger}(\xi) \vert a b\rangle_A \\
&= \langle \xi \vert f(a b)\rangle_A^X \\
&= \langle \xi \vert (f \triangleleft a)(b)\rangle_A^X
\end{aligned}\]
so \(g = (f \triangleleft a)^{\dagger}\).
</par>
<br>
<par>
<b style="color: #1a1a1a;"> (b) Bilinearity.</b>
<br>
Linear in \(f\):
\[((f_1 + f_2) \triangleleft a)(b) = (f_1 + f_2)(a b) = f_1(ab) + f_2(ab) = (f_1 \triangleleft a)(b) + (f_2 \triangleleft a)(b)\]
Linear in \(a\):
\[(f \triangleleft (a_1 + a_2))(b) = f((a_1 + a_2) b) = f(a_1 b) + f(a_2 b) = (f \triangleleft a_1)(b) + (f \triangleleft a_2)(b)\]
using that \(f\) is \(\mathbb{C}\)-linear and A-multiplication distributes.
</par>
<br>
<par>
<b style="color: #1a1a1a;"> (c) Associativity and unitality.</b>
<br>
Associativity:
\[((f \triangleleft a) \triangleleft b)(c) = (f \triangleleft a)(b c) = f(a b c) = (f \triangleleft (a \cdot b))(c)\]
Unitality:
\[(f \triangleleft 1)(b) = f(1 \cdot b) = f(b)\]
So \(\mathcal{H}\) is a right A-module. \(\checkmark\)
</par>
<br>
<par>
<hr style="border: none; border-top: 1px solid black;">

<b style="color: #1a1a1a;">Step 3: \(\mathcal{H}\) has an A-valued inner product.</b> <br>
Define
\[\langle f \vert g \rangle_A := f^{\dagger} \circ g \in End(A_A) = A\]
using the identification \(End(A_A) \cong A\) via \(T \mapsto T(1)\). We check the three axioms.
</par>
<br>
<par>
<b style="color: #1a1a1a;"> A-linear in the second slot.</b>
<br>
We have \(\langle f \vert g \triangleleft a\rangle_A = f^{\dagger} \circ (g \triangleleft a)\). Evaluated at \(b \in A\):
\[f^{\dagger}(g(ab)) = (f^{\dagger} \circ g)(ab) = \langle f \vert g\rangle_A \cdot a \cdot b\]
so as an element of \(A\) (evaluating at \(b = 1\)), this equals \(\langle f \vert g\rangle_A \cdot a\). \(\checkmark\)
</par>
<br>
<par>
<b style="color: #1a1a1a;"> Conjugate-symmetric.</b>
\[\langle f \vert g\rangle_A^* = (f^{\dagger} \circ g)^* = g^{\dagger} \circ (f^{\dagger})^{\dagger} = g^{\dagger} \circ f = \langle g \vert f\rangle_A \; \checkmark\]
</par>
<br>
<par>
<b style="color: #1a1a1a;"> Positive-definite.</b>
<br>
We have \(\langle f \vert f\rangle_A = f^{\dagger} \circ f\), which is positive in \(End(A_A) = A\) as the composite of an operator with its adjoint (Corollary 3.2.21). IT's defif \(f^{\dagger} f = 0\), then for all \(b \in A\),
\[\langle f(b) \vert f(b)\rangle_A^X = \langle b \vert f^{\dagger} f (b)\rangle_A = 0\]
so \(f(b) = 0\) by definiteness of \(\langle \cdot \vert \cdot \rangle_A^X\), hence \(f = 0\). \(\checkmark\)
</par>
<br>
<par>
Therefore \(\mathcal{H} = AdHom(A_A \rightarrow X_A)\) is a right Hilbert \(C^*\)-module. \(\blacksquare\)
</par>
</div>
</div>

<!-- commentary -->

### Correspondences

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #008000;">VecSpace</span><span style="color: #1a1a1a;">, </span><span style="color: #0000FF;">InnerProduct</span><span style="color: #1a1a1a;">)</span></span>
<b style="color: #1a1a1a;">Definition: Correspondence of Unitary Algebras.</b> <br>
Given A,B unitary algebras. An A–B correspondence is an A–B bimodule \({}_{A}X_B\) equipped with a right B-valued inner product \(\langle \cdot \vert \cdot \rangle_B \) such that \(\rho : A \rightarrow End(X_B)\) is a unital \(\star\)–algebra map. Thus,
<br>
$$\forall a \in A, \; \; \eta, \zeta \in X \qquad \qquad \langle a^*\eta\vert\zeta\rangle_B = \langle \eta \vert a \zeta \rangle_B$$
</div>

<!-- commentary -->

From this we can introduce the correct definition of relative tensor product.

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #008000;">VecSpace</span><span style="color: #1a1a1a;">, </span><span style="color: #0000FF;">InnerProduct</span><span style="color: #1a1a1a;">)</span></span>
<b style="color: #1a1a1a;">Definition: Relative Tensor Product of Correspondences.</b> <br>
Given A,B,C unitary algebras and \( {}_{A}X_{B}, {}_B{Y}_{C} \) correspondences. The <b style="color: #1a1a1a;">relative tensor product</b>, \({}_{A}X \boxtimes_B Y_C \), is the quotient space \(X \otimes Y/N \) where
$$N = span\{ \eta b \otimes \zeta - \eta \otimes b \zeta \; \vert \; \eta \in X, \; \zeta \in Y, \; \text{ and } b \in B \} $$
We denote the image of \(\eta \otimes \zeta\) by \(\eta \boxtimes \zeta\), and equip \(X \boxtimes_B Y\) with the \(C\)-valued inner product
$$\langle \eta_1 \boxtimes \zeta_1 \vert \eta_2 \boxtimes \zeta_2 \rangle_C := \langle \langle \eta_2 \vert \eta_1 \rangle_B \, \zeta_1 \vert \zeta_2 \rangle_C.$$
This is well-defined and positive-definite (this is the content of Lemma 3.2.33), so \({}_{A}X \boxtimes_B Y_C\) is again an A–C correspondence.
</div>

<!-- commentary -->

### From Hilbert Space Modules to Correspondences

<!-- commentary: the Connes fusion definition starts from Hilbert *space* modules, not correspondences — this section bridges the gap -->

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold; color: #008000;">HilbertSpace</span>
<b style="color: #1a1a1a;">Definition: Hilbert Space Module.</b> <br>
A right <b style="color: #1a1a1a;">Hilbert space</b> B-module \(H_B\) is a Hilbert space \(H\) equipped with a right B-action, i.e. a unital \(\star\)-homomorphism \(B^{op} \rightarrow B(H)\). Its \(\mathbb{C}\)-valued inner product does <b style="color: #1a1a1a;">not</b> restrict to a canonical B-valued inner product (unless \(B = \mathbb{C}\)); this is the content of Warning 3.3.3.
</div>

<!-- commentary -->

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold;"><span style="color: #1a1a1a;">(</span><span style="color: #008000;">VecSpace</span><span style="color: #1a1a1a;">, </span><span style="color: #0000FF;">InnerProduct</span><span style="color: #1a1a1a;">)</span></span>
<b style="color: #1a1a1a;">Trick: Realization via \(L^2 B\).</b> <br>
Given a Hilbert space module \(H_B\), apply the realization trick with the standard module \(L^2 B\) in place of \(B\). The adjointable maps \(Hom(L^2 B_B \rightarrow H_B)\) form a right Hilbert \(C^*\)-module with B-valued inner product
<br>
$$\langle f \vert g \rangle_B := f^{\dagger} g \in End(L^2 B_B) = B.$$
This converts the Hilbert space module \(H_B\) — which had no canonical B-valued inner product — into a genuine B-correspondence, exactly the kind of object the relative tensor product of correspondences can act on.
</div>

<!-- commentary -->

### Connes Fusion

<!-- commentary: everything is now in place — Connes fusion is just realization (Hom(L^2B -> H)) followed by the relative tensor product of correspondences. We separate the space it produces from the operation that produces it. -->

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold; color: #008000;">HilbertSpace</span>
<b style="color: #1a1a1a;">Definition: Connes Fusion (the Space).</b>
<br>
Given a right B-module \(H_B\) and a left B-module \({}_{B}K\), the <b style="color: #1a1a1a;">Connes fusion relative tensor product Hilbert space</b> \(H \boxtimes_B K\) is
$$ Hom(L^2B_B \rightarrow H_B) \boxtimes_B K$$
equipped with the \(\mathbb{C}\)-valued inner product
$$\langle f_1 \boxtimes \eta_1 \vert f_2 \boxtimes \eta_2 \rangle := \langle \langle f_2 \vert f_1 \rangle_B \eta_1 \vert \eta_2 \rangle_K$$
where
$$\langle f_2 \vert f_1 \rangle_B = f_2^{\dagger}f_1 \in End(L^2B_B)=B.$$
</div>

<!-- commentary -->

<div style="background-color: #ffe4eb; padding: 10px; color: #1a1a1a; position: relative;">
<span style="position: absolute; top: 8px; right: 12px; font-weight: bold; color: #0000FF;">Bifunctor</span>
<b style="color: #1a1a1a;">Definition: Connes Fusion (the Operation).</b>
<br>
Given module maps \(x : H_B \rightarrow M_B\) and \(y : {}_{B}K \rightarrow {}_{B}N\), Connes fusion produces a map
$$x \boxtimes_B y : H \boxtimes_B K \rightarrow M \boxtimes_B N$$
determined by
$$f \boxtimes \eta \mapsto (x \circ f) \boxtimes y\eta$$
for \(f \in Hom(L^2B_B \rightarrow H_B)\) and \(\eta \in K\). Here \(x\) acts on the realized module \(Hom(L^2B_B \rightarrow H_B)\) by post-composition \(f \mapsto x \circ f\). This makes \(\boxtimes_B\) a <b style="color: #1a1a1a;">bifunctor</b>: it acts not only on modules but on the maps between them, and respects composition.
</div>

<!-- commentary -->