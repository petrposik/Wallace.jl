# Wallace

Wallace is a high-performance, easy-to-use evolutionary computation framework written in [Julia](http://julialang.org/), built for researchers, students, and software engineers alike.
To simultaneously achieve performance and ease-of-use, Wallace utilises computational reflection to compile problem-specific data structures and algorithms at run-time, using a beautiful and compact domain-specific language.

**Installation:** ```julia> Pkg.add("Wallace")```

> Note: To avoid installation issues, ensure that the rest of your Julia packages are up-to-date via     `Pkg.update()`.

## Documentation and Tutorials

For technical documentation and an extensive set of tutorials, aimed at a wide range of different audiences, visit the Wallace website at: [http://www.christimperley.co.uk/Wallace.jl](http://www.christimperley.co.uk/Wallace.jl).

Up-to-date documentation and tutorials can be found at:
[wallacejl.readthedocs.org](http://wallacejl.readthedocs.org)

## Usage
To load an example problem in Wallace, follow the code below; a list of example problems can be found by calling the `examples()` function.

```julia
using Wallace

ex = example("one_max")
results = run!(ex)
```
To compose an algorithm specification into executable Julia code tailored to a given problem, follow the example code below:

```julia
algo = compose("my_configuration_file.cfg")
results = run!(algo)
```

## Citation

If you plan on using Wallace for your research, we encourage you to cite the
paper below. Additionally, put in a merge request, and we will add your paper
to the list of papers using Wallace.

```bibtex
@inproceedings{timperley2015wallace,
  author = {Timperley, Christopher Steven and Stepney, Susan},
  title = {Wallace: An efficient generic evolutionary framework},
  booktitle={ECAL 15},
  pages={365--372},
  year={2015},
  organization={MIT Press}
}
```
