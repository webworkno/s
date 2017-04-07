## DESCRIPTION
## intervals of concavity; points of inflection; second derivative
## ENDDESCRIPTION

## Tagged by jjh2b 8/22/06

## DBsubject(Calculus - single variable)
## DBchapter(Applications of differentiation)
## DBsection(Concavity and points of inflection)
## Date(8/23/07)
## Institution(ASU)
## Author(K. Lesh)
## Level(4)
## MO(1)
## TitleText1('Calculus: Early Transcendentals')
## AuthorText1('Stewart')
## EditionText1('5e')
## Section1('4.3')
## Problem1('')
## TitleText2('Calculus: Early Transcendentals')
## AuthorText2('Stewart')
## EditionText2('6')
## Section2('4.3')
## Problem2('')
## KEYWORDS('calculus','concavity','inflection','derivative','inflection point','differentiation', 'second derivative', 'inflection point')

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

$a = 6;
$b = 2;

$f=Formula(" {1}/{$a x^2+$b}  ")->reduce;

$inflection_point1 = -sqrt($b/(3*$a));
$inflection_point2 = sqrt($b/(3*$a));

$ccup=Compute(     "(-infinity, $inflection_point1) , ($inflection_point2, infinity)"        );
$ccdn=List(Interval(     "($inflection_point1,$inflection_point2)"         ));
$xinflects=List(     $inflection_point1, $inflection_point2     );

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
Let \( \displaystyle f(x) = $f \).  Find the open intervals on which \( f \) is concave up (down).  Then determine the \( x\)-coordinates of all inflection points of \( f\).
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
