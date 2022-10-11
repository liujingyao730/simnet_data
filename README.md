# Data Structure Description

The data includes road network data and vehicle count data: the road network data is stored in *.pkl file, which can be loaded by python pickle package; the vehicle count data of each simulation scenario is stored in 8 csv files, identified by the same prefix followed by "_destn", which represents the number of vehicles going to different exits in this simulation scenario.

## Road network data structure

Loading a pkl file using the pickle package in python will get a dict object containing the following five elements.

- 'ordinary_cell':{edge_id: {'cell_length':cell_length, 'cell_id':[id0, id1, ... ]}, ...}

This is the element that stores all the node ids, indexed by the edge in sumo, containing the length of the nodes within this edge and the sequence of node ids within.

- 'connection': [[from1, to1], [from2, to2], ...]

This is the connection between the different edges, represented by the node id

- 'signal_connection': {from_id: {to_id: [start_time, end_time, tlc_index]}}

Information indicating signal changes. It is the start time and end time of green light passage from a node to the corresponding node, and the corresponding signal id, which can be queried to find the signal period and the offset relative to the simulation start time.

- 'tlc_time': [[cycle_time, offset], ...]

## Number of vehicles data

The data of the same simulation scene has the same prefix, followed by "_destn" to indicate the corresponding end point. The first line of each csv file is the node id, from the second line is the number of vehicles in the node at the corresponding time, and the first element of each line is the corresponding time.

It is worth noting that the entrances and exits in each scene are not in the above data file, the exits and entrances corresponding to the four_large.pkl file is as follows:

exits: -gneE0-1, -gneE1-1, -gneE2-2, -gneE4-3, -gneE5-3, -gneE6-1, -gneE12-1, -gneE13-1
entrances: gneE0-0, gneE1-0, gneE2-0, gneE4-0, gneE5-0, gneE6-0, gneE8-0, gneE10-0, gneE12-0, gneE13-0, gneE14-0, gneE15-0

the exits and entrances corresponding to the four_test1.pkl file is as follows:

exits: -gneE0-1, -gneE1-1, -gneE2-2, -gneE4-3, -gneE5-3, -gneE6-1, -gneE8-3, -gneE10-2
entrances: gneE0-0, gneE1-0, gneE2-0, gneE4-0, gneE5-0, gneE6-0, gneE8-0, gneE10-0
