Testing out basic submodule cloning functionality, for tracking multiple copies of the same file with similar history.

Could also use subtree split and merge.

Commands

	git init .
	echo 'Setup' > README.md
	git add -A && git commit -m "Initial commit"

	git checkout --orphan sub/master
	rm README.md
	echo 'Some test file' > test.txt
	git add -A && git commit -m "test: Initial sub commit"

	git checkout master

	# Add submodules
	git submodule add -b sub/master ./ sub
	git submodule add -b sub/master ./ sub_copy

	# Add content
	cd sub
	echo 'Added line' >> test.txt
	git add -A && git commit -m "test: Updated"
	# Push changes to local repo
	git push origin
	cd ..
	git add -A && git commit -m "sub: Updated"

	# Update clone submodule
	cd sub_copy
	git pull origin
	cd ..
	git add -A && git commit -m "sub_copy: Updated"

	# Add subtree
	git subtree add --prefix=sub_subtree sub/master
	cd sub_subtree
	touch biscuit.txt
	git add -A && git commit -m "sub_subtree: Biscuit"
	# Push changes
	git subtree push --prefix=sub_subtree ./  sub/master
	cd ..

	# Update first submodule
	cd sub
	git pull origin
	cd ..
	git add -A && git commit -m "sub: Update from sub_subtree"

