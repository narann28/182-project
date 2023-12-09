# Implementation for Running Team 12 Classic Software Testing
* Step 1: Clone the following repository to your local machine: https://github.com/rohanpadhye/JQF
* Step 2: Install MAVEN and the most up to date version of JDK
* Step 3: Run ./setup.sh to compile any necessary dependencies
* Step 4: Run javac -cp .:$(scripts/classpath.sh) SimpleTest.java to compile the simple java test file
* Step 5: Run bin/jqf-random SimpleTest testSimpleTest 10 to run the testsimpletest function within the SimpleTest.java function and generate 10 random inputs


# JQF + Zest: Semantic Fuzzing for Java
[![Build](https://github.com/rohanpadhye/JQF/actions/workflows/ci.yml/badge.svg)](https://github.com/rohanpadhye/JQF/actions/workflows/ci.yml)

[ISSTA'19 paper]: https://rohan.padhye.org/files/zest-issta19.pdf
[ISSTA'18 paper]: https://rohan.padhye.org/files/perffuzz-issta18.pdf
[ISSTA'19 tool paper]: https://rohan.padhye.org/files/jqf-issta19.pdf
[ICSE'20 paper]: https://rohan.padhye.org/files/rlcheck-icse20.pdf
[ASE'20 paper]: https://rohan.padhye.org/files/bigfuzz-ase20.pdf
[ICSE'21 paper]: https://rohan.padhye.org/files/bonsai-icse21.pdf
[ISSTA'23 paper]: https://dx.doi.org/10.1145/3597926.3598107

JQF is a feedback-directed fuzz testing platform for Java (think: AFL/LibFuzzer but for JVM bytecode). JQF uses the abstraction of *property-based testing*, which makes it nice to write fuzz drivers as parameteric JUnit test methods. JQF is built on top of [junit-quickcheck](https://github.com/pholser/junit-quickcheck). JQF enables running junit-quickcheck style parameterized unit tests with the power of **coverage-guided** fuzzing algorithms such as **Zest**.

[Zest][ISSTA'19 paper] is an algorithm that biases coverage-guided fuzzing towards producing *semantically valid* inputs; that is, inputs that satisfy structural and semantic properties while maximizing code coverage. Zest's goal is to find deep semantic bugs that cannot be found by conventional fuzzing tools, which mostly stress error-handling logic only. By default, JQF runs Zest via the simple command: `mvn jqf:fuzz`.
