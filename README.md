####Lets generate some key pairs + SSH configs! (because laziness):

1. Generate a key pair locally with `ssh-keygen`. Enter in info as you see fit (I named the key 'cannadayr.github' (windows users can use the "Putty" application to generate a keypair, more info can be found via www.chiark.greenend.org.uk/~sgtatham/putty/)

2. Upload the PUBLIC key to your github->settings->SSH keys (copy and paste the entire text)

3. Edit your ~/.ssh/config file with the github host
<pre>
host github.com
        IdentityFile ~/.ssh/[NAME OF PRIVATE KEY]
</pre>
4. Test your connection with `ssh -vT git@github.com` (the 'v' is the verbose flag, useful for debugging)

5. Set your project to use SSH instead of https (run this inside your project directory once)

`git remote set-url origin git@github.com:[USERNAME]/[PROJECTNAME].git`

6. Viola! You should be able to `git push`, and not keep re-entering your account info.

####Make it pretty

1. Edit your ~/.gitconfig and include the following lines
<pre>
[alias]
tree = log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all
</pre>

You can now use `git tree` and it will display your repo all pretty-like
(If you're getting weird escape characters, add the following as well):
<pre>
[core]
pager = less -R 
</pre>

This uses the "less" pager, more info can be found using `man less`. Spoiler, to quit, type `:q[ENTER]` (thats colon,q, then enter)
