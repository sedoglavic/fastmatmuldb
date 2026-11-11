# fastmatmuldb
Fast Matrix Multiplication DataBase

## Refounding Fast Matrix Multiplication State-of-the-Art Tracking

Currently, [fmm.univ-lille.fr](https://fmm.univ-lille.fr) is no longer fully up to date. Furthermore, it should be extended to new kind of results (other coefficient fields or improvement on the constant associated to given exponent).

To maintain FMM SOTA, we need to transition from a centralized site not enough specified to a **decentralized, standardized open-source ecosystem**.

#### Key Proposal Summary

1. **Data Model (Hypergraph Representation):** We propose modeling FMM SOTA as a directed [hypergraph](https://en.wikipedia.org/wiki/Hypergraph) where:
   - **Vertices** represent tensor decompositions (with their matrices sizes, coefficient fields, exponent complexities) and straight-line programs implementing these previous vertices;
   - **Edges** represent construction methods (e.g., Kronecker products, isotopy's action, border rank techniques, path in a flip graph);
   - **A Master File** encodes a summary of the best current results encoded in vertices.

2. **Standardization (JSON Schema):** We need a unified raw data format (e.g., JSON with a clear schema) to store tensor decompositions, arithmetic circuits, and construction rules reliably on one side and FMM SOTA master file on the other.

3. **Decentralized Collaboration:** Instead of a single maintainer, we envision a collaborative model (git-based/blockchain-based) where the theoretical community can contribute, branch, and verify results with proper attribution. FMM SOTA master file could be blockchain based with proof of stakes relying on complexity---constant or exponent---improvement.

#### Next Steps & How to Participate

Participation is completely informal—any feedback or occasional contribution is welcome:

- **Review & Code:** Check out and join the project at [github.com/sedoglavic/fastmatmuldb](https://github.com/sedoglavic/fastmatmuldb).
- **Feedback request:** Do you agree with the hypergraph abstraction? What features or metadata are missing for your use case?

***

**Examples:** In order to be clear, let me list below some examples of vertices and edges:

- [Strassen algorithm](https://link.springer.com/article/10.1007/BF02165411) is a root for practical and historical reason.
- [Winograd variant](https://fmm.univ-lille.fr/2x2x2.html) is a vertex constructed by application of an isotropy to Strassen vertex.
- [Laderman <3x3x3:23>](https://arxiv.org/abs/2512.21980) is a root for historical reason.
- fmm.univ-lille.fr's [<3x3x3:23>](https://fmm.univ-lille.fr/3x3x3.html) is vertex constructed using a [symmetry-based edge](https://arxiv.org/abs/1703.08298) from Winograd 2x2x2 variant vertex. (it is also equivalent to Laderman vertex by an isotropy's action).
- [Perminov's cr58_cn122](https://github.com/dronperminov/FastMatrixMultiplication/blob/master/schemes/results/addition_reduced_ZT/3x3x3_m23_cr58_cn122_ZT_reduced.json) is a vertex (unequivalent to above <3x3x3:23> variants) related to at least two other arithmetic circuit vertices improving the naive constant (first [58](https://arxiv.org/abs/2512.21980) and now [the current best known constant 55](https://arxiv.org/abs/2607.28676)).
- [Smirnov's <3x3x6:40>](https://link.springer.com/article/10.1134/S0965542513120129) is a root (because optimization should not be a derivation rule).
- [Hopcroft-Kerr <2x4x4:26>](https://fmm.univ-lille.fr/2x4x4.html) is a vertex constructed using the Strassen vertex and the [Hopcroft-Kerr construction edge](https://epubs.siam.org/doi/10.1137/0120004).
- [<12x12x12:1040>](https://fmm.univ-lille.fr/12x12x12.html) (as described in fmm.univ-lille.fr) is a vertex constructed using the edge Kronecker product applied to the vertices Hopcroft-Kerr <2x4x4:26> and <6x3x3:40>;
- Kronecker product, direct sum, serendipitous product, ... are edges.

Maybe finite field flip path (and, if some, rational reconstruction) could also be encoded in this hypergraph.

Further extensions to commutative, approximate, semi-field, less inaccurate tensor decomposition are possible.

## First attempt

A tensor-decomposition.schema.json is available for comments.
