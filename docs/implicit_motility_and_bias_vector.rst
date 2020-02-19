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
        E = - \lambda \vec{b} \dot \frac{\vec{\Delta R}}{\|\vec{\Delta R}\|}
    \end{eqnarray}