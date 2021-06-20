
# Failed workflow: find failing step and errors

[Example](https://github.com/lizre/axns/runs/2706797755?check_suite_focus=true)

```{r, eval = FALSE}
Run Rscript -e 'writeLines("text", paste0("data/", "text", ".txt"))'
Error: Error in file(con, "w") : cannot open the connection
Calls: writeLines -> file
In addition: Warning message:
In file(con, "w") :
  cannot open file 'data/text.txt': No such file or directory
Execution halted
Error: Process completed with exit code 1.
```

<br>
<br>

# Test Rscript steps 

by running the part after "run" in Terminal. 
<br>However, working in Terminal doesn't mean the workflow will work.
Many of the failed workflow pushes [here](https://github.com/lizre/axns/commits/main/.github/workflows/workflow.yaml)
worked in the Terminal.
<br>For example, [this one](https://github.com/lizre/axns/commit/da12475e7dcb69d9b80f2a79abf98701c01e2a44#diff-fde0e5d64aae13964fdda6d47af304cf1a7015cbc17e440ac4a5e662ee1d875e):
```{r, eval = FALSE}
- run: Rscript -e 'writeLines("text", paste0("data/", "text", ".txt"))'
```

This `Rscript -e 'writeLines("text", paste0("data/", "text", ".txt"))'` worked
 just fine in Terminal and is very simple, but it would not run as a workflow.

<br>
<br>

# Advanced: act: A debugging tool that runs your workflows locally

https://github.com/nektos/act

