# Python

## Noteworthy Packages

Dealing with data:
- Feather - fast read/write dataframes
- Ibis - interact with data in a SQL like environment
- Paratext - multicore multithreaded CSV read to RAM at 2GB/sec
- Bcolz - efficiently query tables with a large number of columns

Visualising data:
- Altair - declarative data visualisation
- Bokeh - interactive
- Geoplotlib - visualise on map

Cleaning data
- Blaze - numpy for big data
- Xarray - tidy data
- Dask - parallel computing

Machine learning
- Keras - Humane deep learning
- PyMC3 - Markov chain Monte Carlo

## Vector difference timings

```
In [215]: %timeit a=(1,2);b=(3,4);a[0]-b[0], a[1]-b[1]
The slowest run took 7.06 times longer than the fastest. This could mean that an intermediate result is being cached.
1000000 loops, best of 3: 304 ns per loop

In [216]: %timeit a=np.array((1,2));b=np.array((3,4));a-b
The slowest run took 11.91 times longer than the fastest. This could mean that an intermediate result is being cached.
100000 loops, best of 3: 4.52 µs per loop

In [217]: %timeit a=(1,2);b=(3,4);tuple((f-b for f,b in zip(a,b)))
The slowest run took 4.78 times longer than the fastest. This could mean that an intermediate result is being cached.
100000 loops, best of 3: 2.69 µs per loop

In [218]: %timeit a=[1,2];b=[3,4];[f-b for f,b in zip(a,b)]
The slowest run took 5.25 times longer than the fastest. This could mean that an intermediate result is being cached.
1000000 loops, best of 3: 954 ns per loop

In [219]: %timeit a=[1,2];b=[3,4];a[0]-b[0], a[1]-b[1]
The slowest run took 4.93 times longer than the fastest. This could mean that an intermediate result is being cached.
1000000 loops, best of 3: 435 ns per loop

In [220]: %timeit a=(1,2);b=(3,4);a[0]-b[0],a[1]-b[1]
The slowest run took 7.47 times longer than the fastest. This could mean that an intermediate result is being cached.
1000000 loops, best of 3: 309 ns per loop
```