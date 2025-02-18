Simulating MBQC Circuits
========================

In the previous tutorial, you have learned how to create an MBQC circuit using the 
:obj:`MBQCircuit` class. Now, we will use this circuit to run an actual experiment. 
We will use the :obj:`PatternSimulator` class to create a simulator. Let's try it out


.. ipython:: python

    grid_cluster = mp.templates.grid_cluster(3, 5)
    simulator = mp.PatternSimulator(grid_cluster, backend='pennylane')
    print(simulator)

You can specify the simulator you want to use with the keyword argument ``simulator``.
This can be useful if you want to run a circuit on real hardware. 

To run the circuit, we can simply call ``simulator`` with the circuit as an argument.
If the measurement angle of a node is fixed (i.e. the measurement object :obj:`Ment` is
not trainable), you will not need to specify the measurement angle in the call to the
simulator.

.. ipython:: python

    num_angles = len(grid_cluster.trainable_nodes)
    output_state = simulator(np.random.rand(num_angles))
    print(output_state.shape)

If you want to run the circuit with a particular input state, you can specify it with the
keyword argument ``input_state``. 

.. ipython:: python

    random_state = mp.utils.generate_haar_random_states(3)
    simulator.reset(input_state = random_state)
    output_state = simulator(np.zeros(num_angles))
    print(output_state.shape)

    
