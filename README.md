## DESCRIPTION
## intervals of concavity; points of inflection; second derivative
## ENDDESCRIPTION

## Tagged by jjh2b 8/22/06

## DBsubject(Calculus - single variable)
## DBchapter(Applications of differentiation)
## DBsection(Concavity and points of inflection)
## Date(8/23/07)
## Institution(Union College)
## Author(K. Lesh)
## MLT(Concavity_linear_rational)
## MLTleader(1)
## Level(4)
## MO(1)
## KEYWORDS('calculus','concavity','inflection')

DOCUMENT();        # This should be the first executable line in the problem.

loadMacros(
  "PGstandard.pl",
  "PGunion.pl",            # Union College utilities
  "MathObjects.pl",
  "alignedChoice.pl",      # for aligned answer blanks
  "PGcourse.pl",           # Customization file for the course
);

TEXT(beginproblem());

###################################
# Setup

$a = 5;
$b = 7;
$c = 4;

$f=Formula("{$a x - $b} / {x + $c}   ")->reduce;

$ccup=List(Interval(     "(-infinity,-$c)"        ));
$ccdn=List(Interval(     "(-$c,infinity)"         ));
$xinflects=List(     'NONE'     );

###################################
#  Make an aligned list to present Q and A.
###################################

$al = new_aligned_list(ans_rule_len=>35, numbered=>1, tex_spacing=>"3pt", equals=>0);
$al->qa(
  "\(f\) is concave up on the intervals ",    $ccup->cmp,
  "\(f\) is concave down on the intervals ",   $ccdn->cmp,
  "The inflection points occur at \(x\) = ",   $xinflects->cmp,
);

###################################
# Main text

Context()->texStrings;
BEGIN_TEXT
Let \(\displaystyle f(x) = $f \).  Find the open intervals on which \( f \) is concave up (down).  Then determine the \( x\)-coordinates of all inflection points of \( f\).
$PAR
\{$al->print_q\}
$BR
$BBOLD Notes:$EBOLD
In the first two, your answer should either be a single
interval, such as (0,1), a comma separated list of intervals, such as (-inf, 2), (3,4), or the word
${LQ}none$RQ.
$PAR
In the last one, your answer should be a comma separated list of \( x\) values or the word
${LQ}none$RQ.

END_TEXT
Context()->normalStrings;

###################################
# Answer checking

$showPartialCorrectAnswers = 1;
ANS($al->correct_ans);

###################################


;
ENDDOCUMENT();
