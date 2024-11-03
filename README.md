The CPU contains a set of 16 instructions specified for a 16-bit data-path with load/store architecture. 

Memory is byte addressable, even though all accesses (instruction fetches, loads, stores) are restricted to half-word (2-byte), naturally-aligned accesses.

The CPU has a register file, and a 3-bit FLAG register. The register file comprises sixteen 16-bit registers and has 2 read ports and 1 write port. Register $0 is hardwired to 0x0000. The FLAG register contains three bits: Zero (Z), Overflow (V), and Sign (N).

The CPU has caching for instructions and Data,

The processor will have separate single-cycle instruction and data caches, which are byte-addressable. Caches are 2KB (i.e,. 2048B) in size, 2-way set-associative, with cache blocks of 16B each. Correspondingly, the data array would have 128 lines in total, each being 16 bytes wide. The meta-data array would have 128 total entries composed of 64 sets with 2 ways each. Each entry in the meta-data array should contain the tag bits, the valid bit and one bit for LRU replacement.
The cache write policy is write-through and write-allocate. This means that on hits, it writes to the cache and main memory in parallel. On misses it finds the block in main memory and brings that block to the cache, and then re-performs the write (which will now be a cache hit; thus it will write to both cache and memory in parallel).
The cache read policy is to read from the cache for a hit; on a miss, the data is brought back from main memory to the cache and then the required word (from the block) is read out.
The memory module is the same as before, except for the longer read latency and a “data_valid” output bit. A 2-byte write to memory from the processor will take one cycle, while a 2-byte read from memory will take 4 cycles (though read requests can be issued to memory on every cycle).
The cache modules will have the following interface: one 16-bit (2-byte) data input port, one 16-bit (2-byte) data output port, one 16-bit (2-byte) address input port and a one-bit write-enable input signal.
