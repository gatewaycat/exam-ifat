# exam-ifat

To use IFAT (Instant Feedback Assessment Technique) scratch-off scantrons, 
you must match your multiple choice exam to the predetermined key.

This LaTeX package `exam-ifat.sty` allows you to fix the predetermined answer key.
For example, to set the answer key to "D,B,B" write `4,2,2` as below.

    \documentclass[answers]{exam}
    \usepackage{exam-ifat}
    
    %% SET answerkey for given exam here
    \def\answerkey{{{},4,2,2}}
    
    %% SET random seed (optional)
    \PSNuseoldrandom
    \PSNrandseed{21718}
    
    \loadrandomproblems{3}{data}
    
    \begin{document}
    \begin{questions}
    \foreachproblem{\question\thisproblem}
    \end{questions}
    \end{document}

![Example 1](example1.png)

If you change `4,2,2` to `3,2,2`,
notice that the correct answer to Question 1 gets moved to C.

![Example 2](example2.png)

If you change the random seed but keep the `3,2,2`
the questions get shuffled differently,
but notice that the answer key stays "C,B,B".

![Example 3](example3.png)

This package relies on `probsoln.sty` to shuffle the questions
and relies on `pgfmath.sty` to read your answer key `\answerkey`.
In order to support shuffling questions,
questions must be stored in a separate file
and then loaded using `\loadrandomproblems`, as above.
