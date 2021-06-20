
# Failed workflow: find failing step and errors

Use this:
![image](https://user-images.githubusercontent.com/38010821/122679448-e4ef2e80-d1b8-11eb-9112-5a7814bb80b7.png)

It is NOT just viewing the workflow!
<br>
It actually tells you if something is wrong with file:
[example](https://github.com/lizre/learn-actions/actions/runs/954653138/workflow):
![image](https://user-images.githubusercontent.com/38010821/122679478-0b14ce80-d1b9-11eb-83d4-332262d95c62.png)



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

