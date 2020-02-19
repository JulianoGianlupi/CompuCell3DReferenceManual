Implicit Motility Plugin and Bias Vector Stepabble
--------------------------------------------------

Cell movement in CPM is a result of the stochastic process of membrane fluctuations, this results in overall slow cell
movement and cell diffusion. ``Implicit Motility`` together with ``Bias Vector`` tackles the slow movement of cells in CPM with
a biologically justified method.

``Bias Vector Stepabble`` defines a movement bias vector for the cells (``b``). ``b`` is an unitary
vector that defines the preefred direction of motion for the cell, any movement that changes
the center of mass of the cell in this direction is favored.
The bias vector is an abstraction of the internal structures of the cell and cell polarity.

.. note::
    ``Implicit Motility`` loads ``Bias Vector`` even when the latter is not set-up in the simulation
    files, and vice versa.

Implicit Motility
~~~~~~~~~~~~~~~~~

``Implicit Motility Plugin`` defines how favorable movement in the direction of ``b`` is. It
also calculates the change in energy caused by movement,

.. math::
    \begin{eqnarray}
        E = - \lambda_{IM} \vec{b} \dot \frac{\vec{R}}{\|\vec{\Delta R}\|}.
    \end{eqnarray}

The negative sign might seem strange, but it is there because minimization
of energy is favored. ``R`` is the change in center of mass, it is divided by it's own modulus
so that any movement has the same impact. :math: `\lambda` defines the magnitude of the change,
it can be defined  by cell type or by cell ID (each cell can
have it's own value). The ``XML`` syntax for the "by cell type" case is

.. code-block:: xml

    <Plugin Name="ImplicitMotility">
        <MotilityEnergyParameters CellType="Type1" LambdaMotility="15"/>
        <MotilityEnergyParameters CellType="Type2" LambdaMotility="5"/>
        <MotilityEnergyParameters CellType="Type3" LambdaMotility="7.5"/>
   </Plugin>

