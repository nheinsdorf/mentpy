An introduction to Graph States
===============================

Graph states are a type of quantum state that can be represented by a graph :math:`G`.
The state defined by :math:`G` is 

.. math:: |\psi\rangle = \prod_{i,j \in E(G)} CZ_{ij} |+\rangle_i |+\rangle_j,

where :math:`E(G)` is the set of edges of :math:`G`, and :math:`CZ_{ij}` is the controlled-Z gate on qubits :math:`i` and :math:`j`.

GraphState
----------

In ``mentpy`` we can create a graph state using the ``GraphState`` class:

.. ipython:: python

    gr = mp.GraphState()
    gr.add_edges_from([(0, 1), (1, 2), (2, 0)])
    print(gr)

Stabilizers
-----------

Graph states are a particular type of stabilizer state. We can get the stabilizer operators of such state using the ``stabilizers`` method:

.. ipython:: python
    :okwarning:
    
    stabs = gr.stabilizers()
    print(stabs)

To learn how to use graph states as resources for computation, see the :doc:`intro-to-mbqc` tutorial.