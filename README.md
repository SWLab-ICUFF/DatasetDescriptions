#Presentation

This repository contains descriptions of Linked Data datasets using VoID vocabulary and prepared data to perform the empirical experiments for evaluating dataset ranking models. The directory "dataset" contains the dataset descriptions, serialized as an nQuad RDF file, and the directory "prepared_test_data" contains test data for experiments, serialized as *.csv files.

The datasets descriptions include Linksets, classes, properties and topic categories. It mashes up data from DataHub, dataset dumps, VoID files and DBpedia. The DBpedia Spotlight allowed the recognition of named entities in literal values and the linking of each RDF Entity with a list of topic categories. Named entities are directly linked to categories through the predicate dcterms:subject and each topic category is subsumed by others through the predicate skos:broader. A category c is a topic category of an RDF entity iff there exists a property path {e dcterms:subject/skos:broader* c.} from a named entity e of the dataset to c in DBpedia.


Files in the "prepared_test_data" directory are organized in two subdirectories. The first directory called "bayesian-social_network" contains files for evaluating ranking models using algorithms based on Social Networks Analysis and Bayesian Classifiers. The second directory named "cos-j48-jrip" contains files for evaluating ranking models using algorithms based on JRip and J48 classifiers and Cosine Similarity. Each these two directories, in turn, is also organized in subdirectories that splits test data according to the types of features used in the experiments. The directory "5L" contains test data using dataset representations with five linksets, the directory "12C" contains test data using dataset representations with twelve topic categories, "5L12C" contains test data using dataset representations with five linksets and twelve topic categories, and so on.

The *.csv files in "cos-j48-jrip" is split into three series, indexed by {1, 2, 3}, which contain three types of files: Test_i.csv, Traning_i.csv and Relevants_i.csv. The Test_i.csv contains target datasets to which the datasets in ToBRanked_i.csv should be ranked. The Relevants_i.csv contains the relevance degree rel in {0, 1, 2, 3} of each dataset in ToBeRanked_i.csv with respect to the target datasets in Test_i.csv, where the first column is a dataset id of a dataset in Test_i.csv, the second column is a dataset id of a dataset in ToBeRanked_i.csv and the third column is the relevance degree rel.

The three series of the set of files Test_i.csv, ToBeRankes_i.csv and relevants_i.csv are combinations, in a 3-fold cross-validation approach, of the 1113 datasets selected from the Datahub. 

The directory "bayesian-social_network" contains exactly the same data, except that the TF-IDF of the features if replaced with the feature id itself. This files are used to evaluate ranking models on Bayesian Classifiers and Social Network Analisys.

