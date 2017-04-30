<body>

<h1 align="center">dieharder</h1>

<a href="#NAME">NAME</a><br>
<a href="#SYNOPSIS">SYNOPSIS</a><br>
<a href="#dieharder OPTIONS">dieharder OPTIONS</a><br>
<a href="#DESCRIPTION">DESCRIPTION</a><br>
<a href="#QUICK START EXAMPLES">QUICK START EXAMPLES</a><br>
<a href="#P-VALUES AND THE NULL HYPOTHESIS">P-VALUES AND THE NULL HYPOTHESIS</a><br>
<a href="#FILE INPUT">FILE INPUT</a><br>
<a href="#BEST PRACTICE">BEST PRACTICE</a><br>
<a href="#WARNING!">WARNING!</a><br>
<a href="#EXAMPLES">EXAMPLES</a><br>
<a href="#DISPLAY OPTIONS">DISPLAY OPTIONS</a><br>
<a href="#PUBLICATION RULES">PUBLICATION RULES</a><br>
<a href="#ACKNOWLEDGEMENTS">ACKNOWLEDGEMENTS</a><br>
<a href="#COPYRIGHT">COPYRIGHT</a><br>

<hr>


<h2>NAME
<a name="NAME"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em"><b>dieharder
&minus; A testing and benchmarking tool for random number
generators.</b></p>

<h2>SYNOPSIS
<a name="SYNOPSIS"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">dieharder [-a]
[-d dieharder test number] [-f filename] [-B] <br>
[-D output flag [-D output flag] ... ] [-F] [-c separator]
<br>
[-g generator number or -1] [-h] [-k ks_flag] [-l] <br>
[-L overlap] [-m multiply_p] [-n ntuple] <br>
[-p number of p samples] [-P Xoff] <br>
[-o filename] [-s seed strategy] [-S random number seed]
<br>
[-n ntuple] [-p number of p samples] [-o filename] <br>
[-s seed strategy] [-S random number seed] <br>
[-t number of test samples] [-v verbose flag] <br>
[-W weak] [-X fail] [-Y Xtrategy] <br>
[-x xvalue] [-y yvalue] [-z zvalue]</p>

<h2>dieharder OPTIONS
<a name="dieharder OPTIONS"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">-a runs all the
tests with standard/default options to create a</p>

<p style="margin-left:22%;">user-controllable report. To
control the formatting of the report, see -D below. To
control the power of the test (which uses default values for
tsamples that cannot generally be varied and psamples which
generally can) see -m below as a &quot;multiplier&quot; of
the default number of psamples (used only in a -a run).</p>

<p style="margin-left:11%;">-d test number - selects
specific diehard test. <br>
-f filename - generators 201 or 202 permit either raw binary
or</p>

<p style="margin-left:22%;">formatted ASCII numbers to be
read in from a file for testing. generator 200 reads in raw
binary numbers from stdin. Note well: many tests with
default parameters require a lot of rands! To see a sample
of the (required) header for ASCII formatted input, run</p>

<p style="margin-left:22%; margin-top: 1em">dieharder -o -f
example.input -t 10</p>

<p style="margin-left:22%; margin-top: 1em">and then
examine the contents of example.input. Raw binary input
reads 32 bit increments of the specified data stream.
stdin_input_raw accepts a pipe from a raw binary stream.</p>

<p style="margin-left:11%;">-B binary mode (used with -o
below) causes output rands to be written <br>
in raw binary, not formatted ascii. <br>
-D output flag - permits fields to be selected for inclusion
in</p>

<p style="margin-left:22%;">dieharder output. Each flag can
be entered as a binary number that turns on a specific
output field or header or by flag name; flags are
aggregated. To see all currently known flags use the -F
command.</p>

<p style="margin-left:11%;">-F - lists all known flags by
name and number. <br>
-c table separator - where separator is e.g. &rsquo;,&rsquo;
(CSV) or &rsquo; &rsquo; <br>
(whitespace). <br>
-g generator number - selects a specific generator for
testing. Using</p>

<p style="margin-left:22%;">-g -1 causes all known
generators to be printed out to the display.</p>

<p style="margin-left:11%;">-h prints context-sensitive
help -- usually Usage (this message) or a</p>

<p style="margin-left:22%;">test synopsis if entered as
e.g. dieharder -d 3 -h.</p>

<p style="margin-left:11%;">-k ks_flag - ks_flag</p>

<p style="margin-left:22%; margin-top: 1em">0 is fast but
slightly sloppy for psamples &gt; 4999 (default).</p>

<p style="margin-left:22%; margin-top: 1em">1 is MUCH
slower but more accurate for larger numbers of psamples.</p>

<p style="margin-left:22%; margin-top: 1em">2 is slower
still, but (we hope) accurate to machine precision for any
number of psamples up to some as yet unknown numerical upper
limit (it has been tested out to at least hundreds of
thousands).</p>

<p style="margin-left:22%; margin-top: 1em">3 is kuiper ks,
fast, quite inaccurate for small samples, deprecated.</p>

<p style="margin-left:11%;">-l list all known tests. <br>
-L overlap</p>

<p style="margin-left:22%; margin-top: 1em">1 (use overlap,
default)</p>

<p style="margin-left:22%; margin-top: 1em">0 (don&rsquo;t
use overlap)</p>

<p style="margin-left:22%; margin-top: 1em">in operm5 or
other tests that support overlapping and non-overlapping
sample modes.</p>

<p style="margin-left:11%;">-m multiply_p - multiply
default # of psamples in -a(ll) runs to crank</p>

<p style="margin-left:22%;">up the resolution of failure.
-n ntuple - set ntuple length for tests on short bit strings
that permit the length to be varied (e.g. rgb bitdist).</p>

<p style="margin-left:11%;">-o filename - output -t count
random numbers from current generator to <br>
file. <br>
-p count - sets the number of p-value samples per test
(default 100). <br>
-P Xoff - sets the number of psamples that will cumulate
before <br>
deciding</p>

<p style="margin-left:22%;">that a generator is
&quot;good&quot; and really, truly passes even a -Y 2 T2D
run. Currently the default is 100000; eventually it will be
set from AES-derived T2D test failure thresholds for fully
automated reliable operation, but for now it is more a
&quot;boredom&quot; threshold set by how long one might
reasonably want to wait on any given test run.</p>

<p style="margin-left:11%;">-S seed - where seed is a uint.
Overrides the default random seed</p>

<p style="margin-left:22%;">selection. Ignored for file or
stdin input.</p>

<p style="margin-left:11%;">-s strategy - if strategy is
the (default) 0, dieharder reseeds (or</p>

<p style="margin-left:22%;">rewinds) once at the beginning
when the random number generator is selected and then never
again. If strategy is nonzero, the generator is reseeded or
rewound at the beginning of EACH TEST. If -S seed was
specified, or a file is used, this means every test is
applied to the same sequence (which is useful for validation
and testing of dieharder, but not a good way to test rngs).
Otherwise a new random seed is selected for each test.</p>

<p style="margin-left:11%;">-t count - sets the number of
random entities used in each test, where</p>

<p style="margin-left:22%;">possible. Be warned -- some
tests have fixed sample sizes; others are variable but have
practical minimum sizes. It is suggested you begin with the
values used in -a and experiment carefully on a test by test
basis.</p>

<p style="margin-left:11%;">-W weak - sets the
&quot;weak&quot; threshold to make the test(s) more or
less</p>

<p style="margin-left:22%;">forgiving during e.g. a
test-to-destruction run. Default is currently 0.005.</p>

<p style="margin-left:11%;">-X fail - sets the
&quot;fail&quot; threshold to make the test(s) more or
less</p>

<p style="margin-left:22%;">forgiving during e.g. a
test-to-destruction run. Default is currently 0.000001,
which is basically &quot;certain failure of the null
hypothesis&quot;, the desired mode of reproducible generator
failure.</p>

<p style="margin-left:11%;">-Y Xtrategy - the Xtrategy flag
controls the new &quot;test to failure&quot; <br>
(T2F)</p>

<p style="margin-left:22%;">modes. These flags and their
modes act as follows:</p>

<p style="margin-left:22%; margin-top: 1em">0 - just run
dieharder with the specified number of tsamples and
psamples, do not dynamically modify a run based on results.
This is the way it has always run, and is the default.</p>

<p style="margin-left:22%; margin-top: 1em">1 -
&quot;resolve ambiguity&quot; (RA) mode. If a test returns
&quot;weak&quot;, this is an undesired result. What does
that mean, after all? If you run a long test series, you
will see occasional weak returns for a perfect generators
because p is uniformly distributed and will appear in any
finite interval from time to time. Even if a test run
returns more than one weak result, you cannot be certain
that the generator is failing. RA mode adds psamples
(usually in blocks of 100) until the test result ends up
solidly not weak or proceeds to unambiguous failure. This is
morally equivalent to running the test several times to see
if a weak result is reproducible, but eliminates the bias of
personal judgement in the process since the default failure
threshold is very small and very unlikely to be reached by
random chance even in many runs.</p>

<p style="margin-left:22%; margin-top: 1em"><b>This option
should only be used with -k 2.</b></p>

<p style="margin-left:22%; margin-top: 1em">2 - &quot;test
to destruction&quot; mode. Sometimes you just want to know
where or if a generator will .I ever fail a test (or test
series). -Y 2 causes psamples to be added 100 at a time
until a test returns an overall pvalue lower than the
failure threshold or a specified maximum number of psamples
(see -P) is reached.</p>

<p style="margin-left:22%; margin-top: 1em">Note well! In
this mode one may well fail due to the <i>alternate</i> null
hypothesis -- the test itself is a bad test and fails! Many
dieharder tests, despite our best efforts, are numerically
unstable or have only approximately known target statistics
or are straight up asymptotic results, and will eventually
return a failing result even for a gold-standard generator
(such as AES), or for the hypercautious the XOR generator
with AES, threefish, kiss, all loaded at once and
xor&rsquo;d together. It is therefore safest to use this
mode .I comparatively, executing a T2D run on AES to get an
idea of the test failure threshold(s) (something I will
eventually do and publish on the web so everybody
doesn&rsquo;t have to do it independently) and then running
it on your target generator. Failure with numbers of
psamples within an order of magnitude of the AES thresholds
should probably be considered possible test failures, not
generator failures. Failures at levels significantly less
than the known gold standard generator failure thresholds
are, of course, probably failures of the generator.</p>

<p style="margin-left:22%; margin-top: 1em"><b>This option
should only be used with -k 2.</b></p>

<p style="margin-left:11%;">-v verbose flag -- controls the
verbosity of the output for debugging</p>

<p style="margin-left:22%;">only. Probably of little use to
non-developers, and developers can read the enum(s) in
dieharder.h and the test sources to see which flag values
turn on output on which routines. 1 is result in a highly
detailed trace of program activity.</p>

<p style="margin-left:11%;">-x,-y,-z number - Some tests
have parameters that can safely be varied</p>

<p style="margin-left:22%;">from their default value. For
example, in the diehard birthdays test, one can vary the
number of length, which can also be varied. -x 2048 -y 30
alters these two values but should still run fine. These
parameters should be documented internally (where they
exist) in the e.g. -d 0 -h visible notes.</p>

<p style="margin-left:22%; margin-top: 1em"><b>NOTE
WELL:</b> The assessment(s) for the rngs may, in fact, be
completely incorrect or misleading. There are still
&quot;bad tests&quot; in dieharder, although we are working
to fix and improve them (and try to document them in the
test descriptions visible with -g testnumber -h). In
particular, &rsquo;Weak&rsquo; pvalues should occur one test
in two hundred, and &rsquo;Failed&rsquo; pvalues should
occur one test in a million with the default thresholds -
that&rsquo;s what p MEANS. Use them at your Own Risk! Be
Warned!</p>

<p style="margin-left:22%; margin-top: 1em">Or better yet,
use the new -Y 1 and -Y 2 resolve ambiguity or test to
destruction modes above, comparing to similar runs on one of
the as-good-as-it-gets cryptographic generators, AES or
threefish.</p>

<h2>DESCRIPTION
<a name="DESCRIPTION"></a>
</h2>



<p style="margin-left:11%; margin-top: 1em"><b>dieharder</b></p>

<p style="margin-left:11%; margin-top: 1em">Welcome to the
current snapshot of the dieharder random number tester. It
encapsulates all of the Gnu Scientific Library (GSL) random
number generators (rngs) as well as a number of generators
from the R statistical library, hardware sources such as
/dev/*random, &quot;gold standard&quot; cryptographic
quality generators (useful for testing dieharder and for
purposes of comparison to new generators) as well as
generators contributed by users or found in the literature
into a <i>single harness</i> that can time them and subject
them to various tests for randomness. These tests are
variously drawn from George Marsaglia&rsquo;s &quot;Diehard
battery of random number tests&quot;, the NIST Statistical
Test Suite, and again from other sources such as personal
invention, user contribution, other (open source) test
suites, or the literature.</p>

<p style="margin-left:11%; margin-top: 1em">The primary
point of dieharder is to make it easy to time and test
(pseudo)random number generators, including both software
and hardware rngs, with a fully open source tool. In
addition to providing &quot;instant&quot; access to testing
of all built-in generators, users can choose one of three
ways to test their own random number generators or sources:
a unix pipe of a raw binary (presumed random) bitstream; a
file containing a (presumed random) raw binary bitstream or
formatted ascii uints or floats; and embedding your
generator in dieharder&rsquo;s GSL-compatible rng harness
and adding it to the list of built-in generators. The stdin
and file input methods are described below in their own
section, as is suggested &quot;best practice&quot; for
newbies to random number generator testing.</p>

<p style="margin-left:11%; margin-top: 1em">An important
motivation for using dieharder is that the entire test suite
is fully Gnu Public License (GPL) open source code and hence
rather than being prohibited from &quot;looking underneath
the hood&quot; all users are openly encouraged to critically
examine the dieharder code for errors, add new tests or
generators or user interfaces, or use it freely as is to
test their own favorite candidate rngs subject only to the
constraints of the GPL. As a result of its openness,
literally hundreds of improvements and bug fixes have been
contributed by users to date, resulting in a far stronger
and more reliable test suite than would have been possible
with closed and locked down sources or even open sources
(such as STS) that lack the dynamical feedback mechanism
permitting corrections to be shared.</p>

<p style="margin-left:11%; margin-top: 1em">Even small
errors in test statistics permit the <i>alternative</i>
(usually unstated) null hypothesis to become an important
factor in rng testing -- the unwelcome possibility that your
generator is just fine but it is the <i>test</i> that is
failing. One extremely useful feature of dieharder is that
it is at least moderately <i>self validating.</i> Using the
&quot;gold standard&quot; aes and threefish cryptographic
generators, you can observe how these generators perform on
dieharder runs to the same general degree of accuracy that
you wish to use on the generators you are testing. In
general, dieharder tests that consistently fail at any given
level of precision (selected with e.g. -a -m 10) on both of
the gold standard rngs (and/or the better GSL generators,
mt19937, gfsr4, taus) are probably unreliable at that
precision and it would hardly be surprising if they failed
your generator as well.</p>

<p style="margin-left:11%; margin-top: 1em">Experts in
statistics are encouraged to give the suite a try, perhaps
using any of the example calls below at first and then using
it freely on their own generators or as a harness for adding
their own tests. Novices (to either statistics or random
number generator testing) are <i>strongly</i> encouraged to
read the next section on p-values and the null hypothesis
and running the test suite a few times with a more verbose
output report to learn how the whole thing works.</p>

<h2>QUICK START EXAMPLES
<a name="QUICK START EXAMPLES"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">Examples for
how to set up pipe or file input are given below. However,
it is recommended that a user play with some of the built in
generators to gain familiarity with dieharder reports and
tests before tackling their own favorite generator or file
full of possibly random numbers.</p>

<p style="margin-left:11%; margin-top: 1em">To see
dieharder&rsquo;s default standard test report for its
default generator (mt19937) simply run:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder
-a</p>

<p style="margin-left:11%; margin-top: 1em">To increase the
resolution of possible failures of the standard -a(ll) test,
use the -m &quot;multiplier&quot; for the test default
numbers of pvalues (which are selected more to make a full
test run take an hour or so instead of days than because it
is truly an exhaustive test sequence) run:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -a -m
10</p>

<p style="margin-left:11%; margin-top: 1em">To test a
different generator (say the gold standard AES_OFB) simply
specify the generator on the command line with a flag:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
205 -a -m 10</p>

<p style="margin-left:11%; margin-top: 1em">Arguments can
be in any order. The generator can also be selected by
name:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
AES_OFB -a</p>

<p style="margin-left:11%; margin-top: 1em">To apply
<i>only</i> the diehard opso test to the AES_OFB generator,
specify the test by name or number:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
205 -d 5</p>

<p style="margin-left:11%; margin-top: 1em">or</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
205 -d diehard_opso</p>

<p style="margin-left:11%; margin-top: 1em">Nearly every
aspect or field in dieharder&rsquo;s output report format is
user-selectable by means of display option flags. In
addition, the field separator character can be selected by
the user to make the output particularly easy for them to
parse (-c &rsquo; &rsquo;) or import into a spreadsheet (-c
&rsquo;,&rsquo;). Try:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
205 -d diehard_opso -c &rsquo;,&rsquo; -D test_name -D
pvalues</p>

<p style="margin-left:11%; margin-top: 1em">to see an
extremely terse, easy to import report or</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
205 -d diehard_opso -c &rsquo; &rsquo; -D default -D
histogram -D description</p>

<p style="margin-left:11%; margin-top: 1em">to see a
verbose report good for a &quot;beginner&quot; that includes
a full description of each test itself.</p>

<p style="margin-left:11%; margin-top: 1em">Finally, the
dieharder binary is remarkably autodocumenting even if the
man page is not available. All users should try the
following commands to see what they do:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder
-h</p>

<p style="margin-left:11%; margin-top: 1em">(prints the
command synopsis like the one above).</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -a -h
<br>
dieharder -d 6 -h</p>

<p style="margin-left:11%; margin-top: 1em">(prints the
test descriptions only for -a(ll) tests or for the specific
test indicated).</p>

<p style="margin-left:11%; margin-top: 1em">dieharder
-l</p>

<p style="margin-left:11%; margin-top: 1em">(lists all
known tests, including how reliable rgb thinks that they are
as things stand).</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
-1</p>

<p style="margin-left:11%; margin-top: 1em">(lists all
known rngs).</p>

<p style="margin-left:11%; margin-top: 1em">dieharder
-F</p>

<p style="margin-left:11%; margin-top: 1em">(lists all the
currently known display/output control flags used with
-D).</p>

<p style="margin-left:11%; margin-top: 1em">Both beginners
and experts should be aware that the assessment provided by
dieharder in its standard report should be regarded with
great suspicion. It is entirely possible for a generator to
&quot;pass&quot; all tests as far as their individual
p-values are concerned and yet to fail utterly when
considering them all together. Similarly, it is
<i>probable</i> that a rng will at the very least show up as
&quot;weak&quot; on 0, 1 or 2 tests in a typical -a(ll) run,
and may even &quot;fail&quot; 1 test one such run in 10 or
so. To understand why this is so, it is necessary to
understand something of <i>rng testing, p-values, and the
null hypothesis!</i></p>

<h2>P-VALUES AND THE NULL HYPOTHESIS
<a name="P-VALUES AND THE NULL HYPOTHESIS"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">dieharder
returns &quot;p-values&quot;. To understand what a p-value
is and how to use it, it is essential to understand the
<i>null hypothesis,</i> <b>H0.</b></p>

<p style="margin-left:11%; margin-top: 1em">The null
hypothesis for random number generator testing is &quot;This
generator is a perfect random number generator, and for any
choice of seed produces a infinitely long, unique sequence
of numbers that have all the expected statistical properties
of random numbers, to all orders&quot;. Note well that we
<i>know</i> that this hypothesis is technically false for
all software generators as they are periodic and do not have
the correct entropy content for this statement to ever be
true. However, many <i>hardware</i> generators fail a priori
as well, as they contain subtle bias or correlations due to
the deterministic physics that underlies them. Nature is
often <i>unpredictable</i> but it is rarely <i>random</i>
and the two words don&rsquo;t (quite) mean the same
thing!</p>

<p style="margin-left:11%; margin-top: 1em">The null
hypothesis can be <i>practically</i> true, however. Both
software and hardware generators can be &quot;random&quot;
<i>enough</i> that their sequences cannot be distinguished
from random ones, at least not easily or with the available
tools (including dieharder!) Hence the null hypothesis is a
practical, not a theoretically pure, statement.</p>

<p style="margin-left:11%; margin-top: 1em">To test
<b>H0</b> , one uses the rng in question to generate a
sequence of presumably random numbers. Using these numbers
one can generate any one of a wide range of <i>test
statistics</i> -- empirically computed numbers that are
considered <i>random samples</i> that may or may not be
covariant subject to H0, depending on whether overlapping
sequences of random numbers are used to generate successive
samples while generating the statistic(s), drawn from a
known distribution. From a knowledge of the target
distribution of the statistic(s) and the associated
cumulative distribution function (CDF) and the
<i>empirical</i> value of the randomly generated
statistic(s), one can read off the probability of obtaining
the empirical result <i>if the sequence was truly
random,</i> that is, if the null hypothesis is true and the
generator in question is a &quot;good&quot; random number
generator! This probability is the &quot;p-value&quot; for
the particular test run.</p>

<p style="margin-left:11%; margin-top: 1em">For example, to
test a coin (or a sequence of bits) we might simply count
the number of heads and tails in a very long string of
flips. If we assume that the coin is a &quot;perfect
coin&quot;, we expect the number of heads and tails to be
<i>binomially distributed</i> and can easily compute the
probability of getting any particular number of heads and
tails. If we compare our recorded number of heads and tails
from the test series to this distribution and find that the
probability of getting the count we obtained is <i>very
low</i> with, say, way more heads than tails we&rsquo;d
suspect the coin wasn&rsquo;t a perfect coin. dieharder
applies this very test (made mathematically precise) and
many others that operate on this same principle to the
string of random bits produced by the rng being tested to
provide a picture of how &quot;random&quot; the rng is.</p>

<p style="margin-left:11%; margin-top: 1em">Note that the
usual dogma is that if the p-value is low -- typically less
than 0.05 -- one &quot;rejects&quot; the null hypothesis. In
a word, it is improbable that one would get the result
obtained if the generator is a good one. If it is any other
value, one does not &quot;accept&quot; the generator as
good, one &quot;fails to reject&quot; the generator as bad
for this particular test. A &quot;good random number
generator&quot; is hence one that we haven&rsquo;t been able
to make fail <i>yet!</i></p>

<p style="margin-left:11%; margin-top: 1em">This criterion
is, of course, naive in the extreme and <i>cannot be used
with dieharder!</i> It makes just as much sense to reject a
generator that has p-values of 0.95 or more! Both of these
p-value ranges are <i>equally unlikely</i> on any given test
run, and <i>should</i> be returned for (on average) 5% of
all test runs by a <i>perfect</i> random number generator. A
generator that fails to produce p-values less than 0.05 5%
of the time it is tested with different seeds is a
<i>bad</i> random number generator, one that <i>fails</i>
the test of the null hypothesis. Since dieharder returns
over 100 pvalues by default <i>per test,</i> one would
expect any perfectly good rng to &quot;fail&quot; such a
naive test around five times by this criterion in a single
dieharder run!</p>

<p style="margin-left:11%; margin-top: 1em">The p-values
themselves, as it turns out, are test statistics! By their
nature, p-values should be uniformly distributed on the
range 0-1. In 100+ test runs with independent seeds, one
should not be surprised to obtain 0, 1, 2, or even (rarely)
3 p-values less than 0.01. On the other hand obtaining 7
p-values in the range 0.24-0.25, or seeing that 70 of the
p-values are greater than 0.5 should make the generator
highly suspect! How can a user determine when a test is
producing &quot;too many&quot; of any particular value range
for p? Or too few?</p>

<p style="margin-left:11%; margin-top: 1em">Dieharder does
it for you, automatically. One can in fact convert a
<i>set</i> of p-values into a p-value by comparing their
distribution to the expected one, using a Kolmogorov-Smirnov
test against the expected uniform distribution of p.</p>

<p style="margin-left:11%; margin-top: 1em"><i>These</i>
p-values obtained from looking at the distribution of
p-values should in turn be uniformly distributed and could
in principle be subjected to still more KS tests in
aggregate. The distribution of p-values for a <i>good</i>
generator should be <i>idempotent,</i> even across different
test statistics and multiple runs.</p>

<p style="margin-left:11%; margin-top: 1em">A failure of
the distribution of p-values at any level of aggregation
signals trouble. In fact, if the p-values of any given test
are subjected to a KS test, and those p-values are then
subjected to a KS test, as we add more p-values to either
level we will either observe idempotence of the resulting
distribution of p to uniformity, <i>or</i> we will observe
idempotence to a single p-value of <i>zero!</i> That is, a
good generator will produce a roughly uniform distribution
of p-values, in the specific sense that the p-values of the
distributions of p-values are themselves roughly uniform and
so on ad infinitum, while a bad generator will produce a
non-uniform distribution of p-values, and as more p-values
drawn from the non-uniform distribution are added to its KS
test, at some point the failure will be absolutely
unmistakeable as the resulting p-value approaches 0 in the
limit. Trouble indeed!</p>

<p style="margin-left:11%; margin-top: 1em">The question
is, trouble with what? Random number tests are themselves
complex computational objects, and there is a probability
that their code is incorrectly framed or that roundoff or
other numerical -- not methodical -- errors are contributing
to a distortion of the distribution of some of the p-values
obtained. This is not an idle observation; when one works on
writing random number generator testing programs, one is
<i>always</i> testing the tests themselves with
&quot;good&quot; (we hope) random number generators so that
egregious failures of the null hypothesis signal not a bad
generator but an error in the test code. The null hypothesis
above is correctly framed from a <i>theoretical</i> point of
view, but from a <i>real and practical</i> point of view it
should read: &quot;This generator is a perfect random number
generator, and for any choice of seed produces a infinitely
long, unique sequence of numbers that have all the expected
statistical properties of random numbers, to all orders
<b>and</b> this test is a perfect test and returns precisely
correct p-values from the test computation.&quot; Observed
&quot;failure&quot; of this joint null hypothesis
<b>H0&rsquo;</b> can come from failure of either or both of
these disjoint components, and comes from the <i>second</i>
as often or more often than the first during the test
development process. When one cranks up the
&quot;resolution&quot; of the test (discussed next) to where
a generator starts to fail some test one realizes, or should
realize, that development never ends and that new test
regimes will always reveal new failures not only of the
generators but of the code.</p>

<p style="margin-left:11%; margin-top: 1em">With that said,
one of dieharder&rsquo;s most significant advantages is the
control that it gives you over a critical test parameter.
From the remarks above, we can see that we should feel
<i>very uncomfortable</i> about &quot;failing&quot; any
given random number generator on the basis of a 5%, or even
a 1%, criterion, especially when we apply a test
<i>suite</i> like dieharder that returns over 100 (and
climbing) distinct test p-values as of the last snapshot. We
want failure to be unambiguous and reproducible!</p>

<p style="margin-left:11%; margin-top: 1em">To accomplish
this, one can simply crank up its resolution. If we ran any
given test against a random number generator and it returned
a p-value of (say) 0.007328, we&rsquo;d be perfectly
justified in wondering if it is really a good generator.
However, the probability of getting this result isn&rsquo;t
really all that small -- when one uses dieharder for hours
at a time numbers like this will definitely happen quite
frequently and mean nothing. If one runs the <i>same</i>
test again (with a different seed or part of the random
sequence) and gets a p-value of 0.009122, and a third time
and gets 0.002669 -- well, that&rsquo;s three 1% (or less)
shots in a row and <i>that</i> should happen only one in a
million times. One way to clearly resolve failures, then, is
to <i>increase the number of p-values</i> generated in a
test run. If the actual distribution of p being returned by
the test is not uniform, a KS test will <i>eventually</i>
return a p-value that is not some ambiguous 0.035517 but is
instead 0.000000, with the latter produced time after time
as we rerun.</p>

<p style="margin-left:11%; margin-top: 1em">For this
reason, dieharder is <i>extremely conservative</i> about
announcing rng &quot;weakness&quot; or &quot;failure&quot;
relative to any given test. It&rsquo;s internal criterion
for these things are currently p &lt; 0.5% or p &gt; 99.5%
weakness (at the 1% level total) and a <i>considerably</i>
more stringent criterion for failure: p &lt; 0.05% or p &gt;
99.95%. Note well that the ranges are symmetric -- too high
a value of p is just as bad (and unlikely) as too low, and
it is <i>critical</i> to flag it, because it is quite
possible for a rng to be <i>too good,</i> on average, and
not to produce <i>enough</i> low p-values on the full
spectrum of dieharder tests. This is where the final kstest
is of paramount importance, and where the
&quot;histogram&quot; option can be very useful to help you
visualize the failure in the distribution of p -- run
e.g.:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder
[whatever] -D default -D histogram</p>

<p style="margin-left:11%; margin-top: 1em">and you will
see a crude ascii histogram of the pvalues that failed (or
passed) any given level of test.</p>

<p style="margin-left:11%; margin-top: 1em">Scattered
reports of weakness or marginal failure in a preliminary
-a(ll) run should therefore not be immediate cause for
alarm. Rather, they are tests to repeat, to watch out for,
to push the rng harder on using the -m option to -a or
simply increasing -p for a specific test. Dieharder permits
one to increase the number of p-values generated for
<i>any</i> test, subject only to the availability of enough
random numbers (for file based tests) and time, to make
failures unambiguous. A test that is <i>truly</i> weak at -p
100 will almost always fail egregiously at some larger value
of psamples, be it -p 1000 or -p 100000. However, because
dieharder is a research tool and is under perpetual
development and testing, it is <i>strongly suggested</i>
that one always consider the alternative null hypothesis --
that the failure is a failure of the test code in dieharder
itself in some limit of large numbers -- and take at least
some steps (such as running the same test at the same
resolution on a &quot;gold standard&quot; generator) to
ensure that the failure is indeed probably in the rng and
not the dieharder code.</p>

<p style="margin-left:11%; margin-top: 1em">Lacking a
source of <i>perfect</i> random numbers to use as a
reference, validating the tests themselves is not easy and
always leaves one with some ambiguity (even aes or
threefish). During development the best one can usually do
is to rely heavily on these &quot;presumed good&quot; random
number generators. There are a number of generators that we
have theoretical reasons to expect to be extraordinarily
good and to lack correlations out to some known underlying
dimensionality, and that also test out extremely well quite
consistently. By using several such generators and not just
one, one can hope that those generators have (at the very
least) <i>different</i> correlations and should not all
uniformly fail a test in the same way and with the same
number of p-values. When all of these generators
<i>consistently</i> fail a test at a given level, I tend to
suspect that the problem is in the test code, not the
generators, although it is very difficult to be
<i>certain,</i> and many errors in dieharder&rsquo;s code
have been discovered and ultimately fixed in just this way
by myself or others.</p>

<p style="margin-left:11%; margin-top: 1em">One advantage
of dieharder is that it has a number of these &quot;good
generators&quot; immediately available for comparison runs,
courtesy of the Gnu Scientific Library and user contribution
(notably David Bauer, who kindly encapsulated aes and
threefish). I use AES_OFB, Threefish_OFB, mt19937_1999,
gfsr4, ranldx2 and taus2 (as well as &quot;true random&quot;
numbers from random.org) for this purpose, and I try to
ensure that dieharder will &quot;pass&quot; in particular
the -g 205 -S 1 -s 1 generator at any reasonable p-value
resolution out to -p 1000 or farther.</p>

<p style="margin-left:11%; margin-top: 1em">Tests (such as
the diehard operm5 and sums test) that consistently
<i>fail</i> at these high resolutions are flagged as being
&quot;suspect&quot; -- possible failures of the
<i>alternative</i> null hypothesis -- and they are
<i>strongly deprecated!</i> Their results should not be used
to test random number generators pending agreement in the
statistics and random number community that those tests are
in fact valid and correct so that observed failures can
indeed safely be attributed to a failure of the
<i>intended</i> null hypothesis.</p>

<p style="margin-left:11%; margin-top: 1em">As I keep
emphasizing (for good reason!) dieharder is community
supported. I therefore openly ask that the users of
dieharder who are expert in statistics to help me fix the
code or algorithms being implemented. I would like to see
this test suite ultimately be <i>validated</i> by the
general statistics community in hard use in an open
environment, where every possible failure of the testing
mechanism itself is subject to scrutiny and eventual
correction. In this way we will eventually achieve a very
powerful suite of tools indeed, ones that may well give us
very specific information not just about failure but of the
<i>mode</i> of failure as well, just how the sequence tested
deviates from randomness.</p>

<p style="margin-left:11%; margin-top: 1em">Thus far,
dieharder has benefitted tremendously from the community.
Individuals have openly contributed tests, new generators to
be tested, and fixes for existing tests that were revealed
by their own work with the testing instrument. Efforts are
underway to make dieharder more portable so that it will
build on more platforms and faster so that more thorough
testing can be done. Please feel free to participate.</p>

<h2>FILE INPUT
<a name="FILE INPUT"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">The simplest
way to use dieharder with an external generator that
produces raw binary (presumed random) bits is to pipe the
raw binary output from this generator (presumed to be a
binary stream of 32 bit unsigned integers) directly into
dieharder, e.g.:</p>

<p style="margin-left:11%; margin-top: 1em">cat
/dev/urandom | ./dieharder -a -g 200</p>

<p style="margin-left:11%; margin-top: 1em">Go ahead and
try this example. It will run the entire dieharder suite of
tests on the stream produced by the linux built-in generator
/dev/urandom (using /dev/random is not recommended as it is
too slow to test in a reasonable amount of time).</p>

<p style="margin-left:11%; margin-top: 1em">Alternatively,
dieharder can be used to test files of numbers produced by a
candidate random number generators:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -a -g
201 -f random.org_bin</p>

<p style="margin-left:11%; margin-top: 1em">for raw binary
input or</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -a -g
202 -f random.org.txt</p>

<p style="margin-left:11%; margin-top: 1em">for formatted
ascii input.</p>

<p style="margin-left:11%; margin-top: 1em">A formatted
ascii input file can accept either uints (integers in the
range 0 to 2^31-1, one per line) or decimal uniform deviates
with at least ten significant digits (that can be multiplied
by UINT_MAX = 2^32 to produce a uint without dropping
precition), also one per line. Floats with fewer digits will
almost certainly fail bitlevel tests, although they may pass
some of the tests that act on uniform deviates.</p>

<p style="margin-left:11%; margin-top: 1em">Finally, one
can fairly easily wrap any generator in the same (GSL)
random number harness used internally by dieharder and
simply test it the same way one would any other internal
generator recognized by dieharder. This is strongly
recommended where it is possible, because dieharder needs to
use a <i>lot</i> of random numbers to thoroughly test a
generator. A built in generator can simply let dieharder
determine how many it needs and generate them on demand,
where a file that is too small will &quot;rewind&quot; and
render the test results where a rewind occurs suspect.</p>

<p style="margin-left:11%; margin-top: 1em">Note well that
file input rands are delivered to the tests on demand, but
if the test needs more than are available it simply rewinds
the file and cycles through it again, and again, and again
as needed. Obviously this significantly reduces the sample
space and can lead to completely incorrect results for the
p-value histograms unless there are enough rands to run EACH
test without repetition (it is harmless to reuse the
sequence for different tests). Let the user beware!</p>

<h2>BEST PRACTICE
<a name="BEST PRACTICE"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">A frequently
asked question from new users wishing to test a generator
they are working on for fun or profit (or both) is &quot;How
should I get its output into dieharder?&quot; This is a
nontrivial question, as dieharder consumes <i>enormous</i>
numbers of random numbers in a full test cycle, and then
there are features like -m 10 or -m 100 that let one
effortlessly demand 10 or 100 times as many to stress a new
generator even more.</p>

<p style="margin-left:11%; margin-top: 1em"><i>Even with
large file support</i> in dieharder, it is difficult to
provide enough random numbers in a file to really make
dieharder happy. It is therefore <i>strongly suggested that
you either:</i></p>

<p style="margin-left:11%; margin-top: 1em">a) Edit the
output stage of your random number generator and get it to
write its production to stdout as a <i>random bit stream</i>
-- basically create 32 bit unsigned random integers and
write them directly to stdout as e.g. char data or raw
binary. Note that this is <i>not</i> the same as writing raw
floating point numbers (that will not be random at all as a
bitstream) and that &quot;endianness&quot; of the uints
should not matter for the null hypothesis of a
&quot;good&quot; generator, as random bytes are random in
any order. Crank the generator and feed this stream to
dieharder in a pipe as described above.</p>

<p style="margin-left:11%; margin-top: 1em">b) Use the
samples of GSL-wrapped dieharder rngs to similarly wrap your
generator (or calls to your generator&rsquo;s hardware
interface). Follow the examples in the ./dieharder source
directory to add it as a &quot;user&quot; generator in the
command line interface, rebuild, and invoke the generator as
a &quot;native&quot; dieharder generator (it should appear
in the list produced by -g -1 when done correctly). The
advantage of doing it this way is that you can then (if your
new generator is highly successful) contribute it back to
the dieharder project if you wish! Not to mention the fact
that it makes testing it very easy.</p>

<p style="margin-left:11%; margin-top: 1em">Most users will
probably go with option a) at least initially, but be aware
that b) is probably easier than you think. The dieharder
maintainers <i>may</i> be able to give you a hand with it if
you get into trouble, but no promises.</p>

<h2>WARNING!
<a name="WARNING!"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">A warning for
those who are testing files of random numbers. dieharder is
a tool that <i>tests random number generators, not files of
random numbers!</i> It is extremely inappropriate to try to
&quot;certify&quot; a file of random numbers as being random
just because it fails to &quot;fail&quot; any of the
dieharder tests in e.g. a dieharder -a run. To put it
bluntly, if one rejects all such files that fail any test at
the 0.05 level (or any other), the one thing one can be
certain of is that the files in question are <i>not</i>
random, as a truly random sequence would fail any given test
at the 0.05 level 5% of the time!</p>

<p style="margin-left:11%; margin-top: 1em">To put it
another way, any file of numbers produced by a
<i>generator</i> that &quot;fails to fail&quot; the
dieharder suite should be considered &quot;random&quot;,
even if it contains sequences that might well
&quot;fail&quot; any given test at some specific cutoff. One
has to presume that passing the broader tests of the
generator itself, it was determined that the p-values for
the test involved was <i>globally</i> correctly distributed,
so that e.g. failure at the 0.01 level occurs neither more
nor less than 1% of the time, on average, over many many
tests. If one particular file generates a failure at this
level, one can therefore safely presume that it is a
<i>random</i> file pulled from many thousands of similar
files the generator might create that have the correct
distribution of p-values at all levels of testing and
aggregation.</p>

<p style="margin-left:11%; margin-top: 1em">To sum up, use
dieharder to validate your generator (via input from files
or an embedded stream). Then by all means use your generator
to produce files or streams of random numbers. Do not use
dieharder as an accept/reject tool to validate <i>the files
themselves!</i></p>

<h2>EXAMPLES
<a name="EXAMPLES"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">To demonstrate
all tests, run on the default GSL rng, enter:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder
-a</p>

<p style="margin-left:11%; margin-top: 1em">To demonstrate
a test of an external generator of a raw binary stream of
bits, use the stdin (raw) interface:</p>

<p style="margin-left:11%; margin-top: 1em">cat
/dev/urandom | dieharder -g 200 -a</p>

<p style="margin-left:11%; margin-top: 1em">To use it with
an ascii formatted file:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
202 -f testrands.txt -a</p>

<p style="margin-left:11%; margin-top: 1em">(testrands.txt
should consist of a header such as:</p>


<p style="margin-left:11%; margin-top: 1em">#==================================================================
<br>
# generator mt19937_1999 seed = 1274511046 <br>

#==================================================================
<br>
type: d <br>
count: 100000 <br>
numbit: 32 <br>
3129711816 <br>
85411969 <br>
2545911541</p>

<p style="margin-left:11%; margin-top: 1em">etc.).</p>

<p style="margin-left:11%; margin-top: 1em">To use it with
a binary file</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -g
201 -f testrands.bin -a</p>

<p style="margin-left:11%; margin-top: 1em">or</p>

<p style="margin-left:11%; margin-top: 1em">cat
testrands.bin | dieharder -g 200 -a</p>

<p style="margin-left:11%; margin-top: 1em">An example that
demonstrates the use of &quot;prefixes&quot; on the output
lines that make it relatively easy to filter off the
different parts of the output report and chop them up into
numbers that can be used in other programs or in
spreadsheets, try:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -a -c
&rsquo;,&rsquo; -D default -D prefix</p>

<h2>DISPLAY OPTIONS
<a name="DISPLAY OPTIONS"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">As of version
3.x.x, dieharder has a single output interface that produces
tabular data per test, with common information in headers.
The display control options and flags can be used to
customize the output to your individual specific needs.</p>

<p style="margin-left:11%; margin-top: 1em">The options are
controlled by binary flags. The flags, and their text
versions, are displayed if you enter:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder
-F</p>

<p style="margin-left:11%; margin-top: 1em">by itself on a
line.</p>

<p style="margin-left:11%; margin-top: 1em">The flags can
be entered all at once by adding up all the desired option
flags. For example, a very sparse output could be selected
by adding the flags for the test_name (8) and the associated
pvalues (128) to get 136:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -a -D
136</p>

<p style="margin-left:11%; margin-top: 1em">Since the flags
are cumulated from zero (unless no flag is entered and the
default is used) you could accomplish the same display
via:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -a -D
8 -D pvalues</p>

<p style="margin-left:11%; margin-top: 1em">Note that you
can enter flags by value or by name, in any combination.
Because people use dieharder to obtain values and then with
to export them into spreadsheets (comma separated values) or
into filter scripts, you can chance the field separator
character. For example:</p>

<p style="margin-left:11%; margin-top: 1em">dieharder -a -c
&rsquo;,&rsquo; -D default -D -1 -D -2</p>

<p style="margin-left:11%; margin-top: 1em">produces output
that is ideal for importing into a spreadsheet (note that
one can subtract field values from the base set of fields
provided by the default option as long as it is given
first).</p>

<p style="margin-left:11%; margin-top: 1em">An interesting
option is the -D prefix flag, which turns on a field
identifier prefix to make it easy to filter out particular
kinds of data. However, it is equally easy to turn on any
particular kind of output to the exclusion of others
directly by means of the flags.</p>

<p style="margin-left:11%; margin-top: 1em">Two other flags
of interest to novices to random number generator testing
are the -D histogram (turns on a histogram of the underlying
pvalues, per test) and -D description (turns on a complete
test description, per test). These flags turn the output
table into more of a series of &quot;reports&quot; of each
test.</p>

<h2>PUBLICATION RULES
<a name="PUBLICATION RULES"></a>
</h2>



<p style="margin-left:11%; margin-top: 1em"><b>dieharder</b>
is entirely original code and can be modified and used at
will by any user, provided that:</p>

<p style="margin-left:11%; margin-top: 1em">a) The original
copyright notices are maintained and that the source,
including all modifications, is made publically available at
the time of any derived publication. This is open source
software according to the precepts and spirit of the Gnu
Public License. See the accompanying file COPYING, which
also must accompany any redistribution.</p>

<p style="margin-left:11%; margin-top: 1em">b) The primary
author of the code (Robert G. Brown) is appropriately
acknowledged and referenced in any derived publication. It
is strongly suggested that George Marsaglia and the Diehard
suite and the various authors of the Statistical Test Suite
be similarly acknowledged, although this suite shares no
actual code with these random number test suites.</p>

<p style="margin-left:11%; margin-top: 1em">c) Full
responsibility for the accuracy, suitability, and
effectiveness of the program rests with the users and/or
modifiers. As is clearly stated in the accompanying
copyright.h:</p>

<p style="margin-left:11%; margin-top: 1em">THE COPYRIGHT
HOLDERS DISCLAIM ALL WARRANTIES WITH REGARD TO THIS
SOFTWARE, INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS, IN NO EVENT SHALL THE COPYRIGHT
HOLDERS BE LIABLE FOR ANY SPECIAL, INDIRECT OR CONSEQUENTIAL
DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF
USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT,
NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF OR IN
CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.</p>

<h2>ACKNOWLEDGEMENTS
<a name="ACKNOWLEDGEMENTS"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">The author of
this suite gratefully acknowledges George Marsaglia (the
author of the diehard test suite) and the various authors of
NIST Special Publication 800-22 (which describes the
Statistical Test Suite for testing pseudorandom number
generators for cryptographic applications), for excellent
descriptions of the tests therein. These descriptions
enabled this suite to be developed with a GPL.</p>

<p style="margin-left:11%; margin-top: 1em">The author also
wishes to reiterate that the academic correctness and
accuracy of the implementation of these tests is his sole
responsibility and not that of the authors of the Diehard or
STS suites. This is especially true where he has seen fit to
modify those tests from their strict original
descriptions.</p>

<h2>COPYRIGHT
<a name="COPYRIGHT"></a>
</h2>


<p style="margin-left:11%; margin-top: 1em">GPL 2b; see the
file COPYING that accompanies the source of this program.
This is the &quot;standard Gnu General Public License
version 2 or any later version&quot;, with the one minor
(humorous) &quot;Beverage&quot; modification listed below.
Note that this modification is probably not legally
defensible and can be followed really pretty much according
to the honor rule.</p>

<p style="margin-left:11%; margin-top: 1em">As to my
personal preferences in beverages, red wine is great, beer
is delightful, and Coca Cola or coffee or tea or even milk
acceptable to those who for religious or personal reasons
wish to avoid stressing my liver.</p>

<p style="margin-left:11%; margin-top: 1em"><b>The Beverage
Modification to the GPL:</b></p>

<p style="margin-left:11%; margin-top: 1em">Any satisfied
user of this software shall, upon meeting the primary
author(s) of this software for the first time under the
appropriate circumstances, offer to buy him or her or them a
beverage. This beverage may or may not be alcoholic,
depending on the personal ethical and moral views of the
offerer. The beverage cost need not exceed one U.S. dollar
(although it certainly may at the whim of the offerer:-) and
may be accepted or declined with no further obligation on
the part of the offerer. It is not necessary to repeat the
offer after the first meeting, but it can&rsquo;t
hurt...</p>
<hr>
</body>
</html>
