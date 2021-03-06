# Tetrahedra_Integration
A function that performs the tetrahedron method of integration in the Brillouin zone.

This function performs Brillouin zone integration of the energy bands to determine the total energy. An improved version of the tetrahedron method is used.
    
This function is an implementation of the algorithm proposed in "Improved tetrahedron method for Brillouin-zone integrations" by Peter E. Blöchl, O. Jepsen, and O. K. Andersen from Physical Review B 49, 16223 – Published 15 June 1994. It is modified in that the submesh vectors (grid_vecs) are not necessarily the reciprocal lattice vectors divided by an integer.

Args:
    r_lattice_vectors (NumPy array): the reciprocal lattice vectors. Each column of the array is one of the vectors.
    grid_vecs (NumPy array): the vectors used to create the grid of k points. All grid points are an integer 
        combination of these vectors. Each column of the array is one of the vectors.
    grid (list of lists of floats): the coordinates of each k point in the reciprocal lattice unit cell at which 
        calculations will be performed.
    PP (function): calculates the first n energy levels at a given k point using the pseudopotential method. PP has 
        two arguments. For its first argument, PP takes a list of floats containing the coordinates of the k point 
        to evaluate the energy levels at. For its second argument, PP takes the number of eigenvalues (equivalent to 
        the number of energy levels) to return. It returns a sorted list (from least to greatest) of the first n 
        eigenvalues (energy values) at that point.
    valence_electrons (int): the number of valence electrons possessed by the element in question.
    apply_weight_correction (bool): true if the integration weights should be corrected to take curvature into 
        account, false otherwise.
    
Returns:
    E_Fermi (float): the calculated Fermi energy level.
    total_energy (float): the total calculated energy in the Brillouin zone, the result of the integration.
