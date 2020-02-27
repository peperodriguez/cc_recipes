# cc_recipes
My personal Clear Case cheatsheet

## Views
Setting the working view:

    ct setview <view_name>

Removing a view (don't forget to save the cs!):

    ct rmview -tag <view_name>
    
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

## Elements
Add a directory to a cc project:

    ct mkelem -mkpath <dir_name>
    
Add a file to a cc project:

    ct mkelem -nc <file_name>
    
Search for elements created in a time window:

    ct find . -version "{created_since(dd1-mm1-yyyy1) && \!created_since(dd2_mm2_yyyy2)}" -print
    
Clean a view of all untracked files (use with due care):

    ct lsprivate | grep -v checkedout | xargs /bin/rm -rf
    
Find /0 elements that are LATEST in <branch_name>:

    ct find . -type f -version "version(.../<branch_name>/LATEST)&&version(.../<branch_name>/0)" -print
    
List all checkouts done by me in a view:

    ct lsc -me -cvi -a
    
List history of an element, with the following format:
"\<element_path\> \<version\> ; \<date\> \<author\> \<operation\> : \<comment\>"
	
    ct lsh -fmt "%En %Vn \t; %Sd %u %o: %c\n" <element_path>
   

### Comparing elements based on labels

List elements labelled `B` whose version in label `A` is different from label `B`:

	ct find -all -element "{lbtype_sub(A) && lbtype_sub(B)}" -version "{lbtype(A) && ! lbtype(B)}" -print
	
Sometimes, to list *ALL* objects of a kind, you need to filter them by *NOT* having a "dummy" label:

    ct find . -version "{version(main/LATEST) && ! lbtype(dummy_label_here)}" -print

## Labels
Always unlock the label you plan to work with:
    
    ct unlock lbtype:<label_name>

Remove a label from file

    ct rmlabel <label_name> <file_name>@@/<branch_name>/<vers>
    
Add a label to a version

    ct mklabel <label_name> <file_name>@@/<branch_name>/<vers>
    
## Branching
Remove a file from a branch

    ct rmbranch <file_name>@@/main/<branch_name>
    
