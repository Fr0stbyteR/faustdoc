# Faust Compiler Options
## FAUST compiler version 2.27.1
~~~faust-options
usage : faust [options] file1 [file2 ...].
        where options represent zero or more compiler options 
	and fileN represents a Faust source file (.dsp extension).
~~~
## Input options:
---------------------------------------
~~~faust-options
  -a <file>                               wrapper architecture file.
  -i        --inline-architecture-files   inline architecture files.
  -A <dir>  --architecture-dir <dir>      add the directory <dir> to the architecture search path.
  -I <dir>  --import-dir <dir>            add the directory <dir> to the import search path.
  -L <file> --library <file>              link with the LLVM module <file>.
  -t <sec>  --timeout <sec>               abort compilation after <sec> seconds (default 120).
~~~
## Output options:
---------------------------------------
~~~faust-options
  -o <file>                               the output file.
  -e        --export-dsp                  export expanded DSP (with all included libraries).
  -uim      --user-interface-macros       add user interface macro definitions to the output code.
  -xml                                    generate an XML description file.
  -json                                   generate a JSON description file.
  -O <dir>  --output-dir <dir>            specify the relative directory of the generated output code and of additional generated files (SVG, XML...).
~~~
## Code generation options:
---------------------------------------
~~~faust-options
  -lang <lang> --language                 select output language,
                                          'lang' should be in c, ocpp, cpp (default), rust, java, llvm, cllvm, fir, wast/wasm, soul, interp.
  -single     --single-precision-floats   use single precision floats for internal computations (default).
  -double     --double-precision-floats   use double precision floats for internal computations.
  -quad       --quad-precision-floats     use quad precision floats for internal computations.
  -es 1|0     --enable-semantics 1|0      use enable semantics when 1 (default), and simple multiplication otherwise.
  -lcc        --local-causality-check     check causality also at local level.
  -light      --light-mode                do not generate the entire DSP API.
  -clang      --clang                     when compiled with clang/clang++, adds specific #pragma for auto-vectorization.
  -flist      --file-list                 use file list used to eval process.
  -exp10      --generate-exp10            pow(10,x) replaced by possibly faster exp10(x).
  -os         --one-sample                generate one sample computation.
  -cn <name>  --class-name <name>         specify the name of the dsp class to be used instead of mydsp.
  -scn <name> --super-class-name <name>   specify the name of the super class to be used instead of dsp.
  -pn <name>  --process-name <name>       specify the name of the dsp entry-point instead of process.
  -lb         --left-balanced             generate left balanced expressions.
  -mb         --mid-balanced              generate mid balanced expressions (default).
  -rb         --right-balanced            generate right balanced expressions.
  -mcd <n>    --max-copy-delay <n>        threshold between copy and ring buffer implementation (default 16 samples).
  -dlt <n>    --delay-line-threshold <n>  threshold between 'mask' and 'select' ring buffer implementation (default INT_MAX samples).
  -mem        --memory                    allocate static in global state using a custom memory manager.
  -ftz <n>    --flush-to-zero <n>         code added to recursive signals [0:no (default), 1:fabs based, 2:mask based (fastest)].
  -inj <f>    --inject <f>                inject source file <f> into architecture file instead of compile a dsp file.
  -scal      --scalar                     generate non-vectorized code.
  -inpl      --in-place                   generates code working when input and output buffers are the same (scalar mode only).
  -vec       --vectorize                  generate easier to vectorize code.
  -vs <n>    --vec-size <n>               size of the vector (default 32 samples).
  -lv <n>    --loop-variant <n>           [0:fastest (default), 1:simple].
  -omp       --openmp                     generate OpenMP pragmas, activates --vectorize option.
  -pl        --par-loop                   generate parallel loops in --openmp mode.
  -sch       --scheduler                  generate tasks and use a Work Stealing scheduler, activates --vectorize option.
  -ocl       --opencl                     generate tasks with OpenCL (experimental).
  -cuda      --cuda                       generate tasks with CUDA (experimental).
  -dfs       --deep-first-scheduling      schedule vector loops in deep first order.
  -g         --group-tasks                group single-threaded sequential tasks together when -omp or -sch is used.
  -fun       --fun-tasks                  separate tasks code as separated functions (in -vec, -sch, or -omp mode).
  -fm <file> --fast-math <file>           use optimized versions of mathematical functions implemented in <file>.
                                          use 'faust/dsp/fastmath.cpp' when file is 'def'.
  -ns <name> --namespace <name>           generate C++ code in a namespace <name>.
  -mapp      --math-approximation         simpler/faster versions of 'floor/ceil/fmod/remainder' functions.
~~~
## Block diagram options:
---------------------------------------
~~~faust-options
  -ps        --postscript                 print block-diagram to a postscript file.
  -svg       --svg                        print block-diagram to a svg file.
  -sd        --simplify-diagrams          try to further simplify diagrams before drawing.
  -drf       --draw-route-frame           draw route frames instead of simple cables.
  -f <n>     --fold <n>                   threshold to activate folding mode during block-diagram generation (default 25 elements).
  -fc <n>    --fold-complexity <n>        complexity threshold to fold an expression in folding mode (default 2)
  -mns <n>   --max-name-size <n>          threshold during block-diagram generation (default 40 char).
  -sn        --simple-names               use simple names (without arguments) during block-diagram generation.
  -blur      --shadow-blur                add a shadow blur to SVG boxes.
~~~
## Math doc options:
---------------------------------------
~~~faust-options
  -mdoc       --mathdoc                   print math documentation of the Faust program in LaTeX format in a -mdoc folder.
  -mdlang <l> --mathdoc-lang <l>          if translation file exists (<l> = en, fr, ...).
  -stripmdoc  --strip-mdoc-tags           strip mdoc tags when printing Faust -mdoc listings.
~~~
## Debug options:
---------------------------------------
~~~faust-options
  -d          --details                   print compilation details.
  -time       --compilation-time          display compilation phases timing information.
  -tg         --task-graph                print the internal task graph in dot format.
  -sg         --signal-graph              print the internal signal graph in dot format.
  -norm       --normalized-form           print signals in normalized form and exit.
  -ct         --check-table               check table index range and fails.
  -cat        --check-all-table           check all table index range.
~~~
## Information options:
---------------------------------------
~~~faust-options
  -h          --help                      print this help message.
  -v          --version                   print version information and embedded backends list.
  -libdir     --libdir                    print directory containing the Faust libraries.
  -includedir --includedir                print directory containing the Faust headers.
  -archdir    --archdir                   print directory containing the Faust architectures.
  -dspdir     --dspdir                    print directory containing the Faust dsp libraries.
  -pathslist  --pathslist                 print the architectures and dsp library paths.
~~~
## Example:
---------------------------------------
~~~faust-options
faust -a jack-gtk.cpp -o myfx.cpp myfx.dsp
~~~
