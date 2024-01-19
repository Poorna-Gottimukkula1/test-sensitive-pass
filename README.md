# Test repo for removing the sensitive passwords/data

This repo is to demonstarte the removal of senstive data using the [BFG](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository#using-the-bfg)


To initiate the process, place the sensitive data(pushed data) inside a file named `password.txt` that needs to be removed from the repository.

For example: 
Dummy pushed token is - `TEST_TOKEN_DUMMY = "hellopassword"`

- Create the password.txt file using the below command.
```
echo "hellopassword" > password.txt
```
- Clone the repository where you pushed the sensitive data by mistakenly and navigate to its directory.
```
git clone git@github.com:<user/org>/test-sensitive-pass.git
cd test-sensitive-pass
```
- Wherever it can be found in your repository's history: Run below commands to replace all text listed in `passwords.txt` 
```
bfg --replace-text ../password.txt
git reflog expire --expire=now --all && git gc --prune=now --aggressive
git push -f origin
```

 #### Other references: 
- Youtube tutorial: https://youtu.be/hseEfxCHzYw?si=sWO-8mlWMQgy3_am.
- bfg installation using brew https://formulae.brew.sh/formula/bfg.
- https://github.com/rtyley/bfg-repo-cleaner/issues/191#issuecomment-448731540.

