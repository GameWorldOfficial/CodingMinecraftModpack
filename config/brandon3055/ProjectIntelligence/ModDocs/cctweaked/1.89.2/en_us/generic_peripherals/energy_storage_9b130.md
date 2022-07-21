energy_storage
Methods for interacting with blocks using Forge's energy storage system.

This works with energy storage blocks, as well as generators and machines which consume energy.

🛈 NOTE
Due to limitations with Forge's energy API, it is not possible to measure throughput (i.e. RF used/generated per tick).

getEnergy()	Get the energy of this block.
getEnergyCapacity()	Get the maximum amount of energy this block can store.
getEnergy()
Source
Get the energy of this block.

Returns
number The energy stored in this block, in FE.
getEnergyCapacity()
Source
Get the maximum amount of energy this block can store.

Returns
number The energy capacity of this block.