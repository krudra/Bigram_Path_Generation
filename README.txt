################################################################## Path generation step ########################################################################
Step 1:
	Download kenlm package from https://kheafield.com/code/kenlm/ and build
	pip3 install https://github.com/kpu/kenlm/archive/master.zip [https://github.com/kpu/kenlm]

Step 2:
        python make_tagging.py <intermediate file (generate from extractive step)> <tagged file>
	Download Twitter POS Tagger and set the path in line 4
        Sample run: python3 make_tagging.py sample_file.txt sample_tagged_file.txt
	Sample file type: Tweet ID \t Tweet Text \t Confidence Score
	Confidence Score is not required for path generation

Step 3:
        1. Go to directory path_compute
	2. In Generate_Path.py adjust the path of language model (lm/test.arpa) [Line: 78]
        3. Run follwing path generation and ranker code: python Generate_Path.py <tagged file>
                Sample run: python3 Generate_Path.py sample_tagged_file.txt
        4. Two files are generated => a. sample_tagged_file.txt_paths b. sample_tagged_file.txt_details.txt

        Note: Structure of path file: path \t average similarity of tweets which generate this path \t linguistic score of the path \t number of tweets combined to generate the path \t length of the path \t centroid score of the path


Packages
--------
nltk
sklearn
scipy
numpy
pypi-kenlm
networkx
snowballstemmer
