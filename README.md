## Characterizing the evolution of user interests
### Channel embedding
    
    
Based on the YouTube comments from 2005 to 2019 this project consists of characterizing the evolution of user interest. In order to find and analyse the communities in this huge social platform, we have to perform an embedding at the video level and an embedding at the channel level. Naturally, the two embeddings should share common characteristics which would determine the behaviour of users on YouTube. This work done on this project focuses on the channel embedding while a parallel work focuses on the video embedding. Results are expected to be shared and combined together in the end.

Files Description:


    ├── bipartite_graph                   # Folder corresponding to the bipartite graph implementation
    |   ├── ... not used for the final embedding
    |
    ├── helpers                           # Folder corresponding to the implementation of SGNS
    │   ├── create_helper_files.ipynb                                 # Create data if we want to modify the minimum number of comments per channel
    │   ├── config_threshold_value.py                                 # Parameters for the minimum number of comments per channel
    │   ├── helpers_channel_embedding.py                              # Helper to compute the jumper and the position ratio
    │   ├── helpers_channels_more_10k.py                              # Helper file for channels having more than 10k comments
    │   ├── helpers_channels_more_300.py                              # Helper file for channels having more than 300 comments
    │   ├── helpers_channels_more_300.py                              # Helper file to visualize the axis projection method
    |
    ├── bipartite_graph                   # Folder corresponding to the proximity graph implementation
    |   ├── ... not used for the final embedding
    |
    ├── word2vec                          # Folder using the word2vecf open source code
    |   ├── ... not used for the final embedding
    |
    ├── word2vec_pytorch                  # Folder corresponding to the implementation of SGNS
    │   ├── creates_training_data             # Folder where the training samples are constructed
    |   |   ├── preprocessing_file_gen_then_sample.ipynb              # First generate the pairs then sample
    |   |   ├── preprocessing_file_gen_then_weighted_sample.ipynb     # First generate the pairs then sample according to a weighted scheme
    |   |   ├── preprocessing_file_sample_then_gen.ipynb              # First sample then generate the pairs from the selected channels
    │   ├── embedding_space              # Folder keeping track of the results
    |   |   ├── ...
    │   ├── main.ipynb                                                # Notebook doingg the training processes
    │   ├── config.py                                                 # Parameters about the training and the result paths
    │   ├── model.py                                                  # Model used
    └── data_analysis.ipynb                                           # Analyses on the number of comments per channel            


### How to run and create an embedding:

- Setup the parameters of the model under `word2vec_pytorch/config.py`.
- Create the training data under the folder `creates_training_data` by running one
of `preprocessing_file_gen_all_comb_then_sample.ipynb`,
`preprocessing_file_gen_all_comb_then_weighted_sample.ipynb`,
`preprocessing_file_sample_then_gen_comb.ipynb` depending on how you want
to generate the training samples.
- Run main.ipynb to create the channel embedding, the embedding will be stored in EMBEDDING_PATH (parameter in config.py)

### How to evaluate the performance of the embedding:
- Create `check_embedding_space.ipynb` and `axis_projection.ipynb` similar to the existing embeddings if they do not exist
- Run `check_embedding_space.ipynb` and `axis_projection.ipynb` with the PATH being the path where the embedding is stored

Two configurations are possible for now:
- Channels having more than 10k comments per channel
- Channels having more than 300 comments per channel

### If you want to select channels having more than k comments per channel (k > 300):
- Modify the THRESHOLD and THRESHOLD_NAME parameter in `helpers/config_threshold_value.py` with the new threshold
- Run `data_analysis.ipynb`
- Run `helpers/create_helper_files.ipynb`
- Create a file similar to `helpers/helpers_channels_more_300.py` for the new THRESHOLD value.
- Run the part "How to run and create an embedding", importing the helper file created above
- Run the part "How to evaluate the performance of the embedding", importing the helper file created above
