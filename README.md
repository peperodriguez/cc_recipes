# cc_recipes
My personal Clear Case cheatsheet

Setting the working view:

    ct setview <view_name>

Removing a view (don't forget to save the cs!):

    ct rmview -tag <view_name>
    
Clean a view of all untracked files (use with due care):

    ct lsprivate | grep -v checkedout | xargs /bin/rm -rf
    
List name of actual view:

    ct pwv
    
List available views (depending on environment can be load-intense):

    ct lsview
    
Get properties for a view:

    ct lsview -pro -ful <view_name>

## Configspec
Dump actual view's configspec:

    ct catcs
    
Edit actual view's configspec with default editor:

    ct edcs
    
Set the configspec to a certain file:

    ct setcs <file_name>
