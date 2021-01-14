
    
    
Based on the YouTube comments from 2005 to 2019 this project consists of characterizing the evolution if user interest. In order to find and analyse the communities in this huge social platform, we have to perform an embedding at the video level and an embedding at the channel level. Naturally, the two spaces should share common characteristics which would determine the behaviour of users on YouTube. This work done on this project focuses on the channel embedding while a parallel work focuses on the video embedding. Results are expected to be shared and combined together in the end.

File Description:


    ├── bipartite_graph                   # Folder corresponding to the bipartite graph implementation
    |   ├── ... not used for the final embedding
    |
    ├── helpers                           # Folder corresponding to the implementation of SGNS
    │   ├── create_helper_files.ipynb               # Create data if we want to modify the minimum number of comments per channel
    │   ├── config_threshold_value.py               # Parameters for the minimum number of comments per channel
    │   ├── helpers_channel_embedding.py            # Helper to compute the jumper and the position ratio
    │   ├── helpers_channels_more_10k.py            # Helper file for channels having more than 10k comments
    │   ├── helpers_channels_more_300.py            # Helper file for channels having more than 300 comments
    │   ├── helpers_channels_more_300.py            # Helper file to visualize the axis projection method
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
    │   ├── main.ipynb                        # Notebook doingg the training processes
    │   ├── config.py                         # Parameters about the training and the result paths
    │   ├── model.py                          # Model used
    └── ...


How to run and create an embedding:

- Setup the parameters of the model under `config.py`:
- Create the training data under the folder `creates_training_data`and run one
of `preprocessing_file_gen_all_comb_then_sample.ipynb`,
`preprocessing_file_gen_all_comb_then_weighted_sample.ipynb`,
`preprocessing_file_sample_then_gen_comb.ipynb` depending on how you want
to generate the training samples.
- Run main.ipynb to create the channel embedding

How to evaluate the performance of the embedding:
- Create a folder similar to 'embedding_space/channel_sampling_then_permutation/CONTEXT_True_20_SUBSAMPLING_False/'
and modify the PATH parameter with the path of the embedding
- Run `check_embedding_space.ipynb` and `axis_projection.ipynb`

Two configurations are possible for now:
- Channels having more than 10k comments per channel
- Channels having more than 300 comments per channel

If you want to select channels having more than k comments per channel (k > 300):
- Modify the THRESHOLD and THRESHOLD_NAME parameter in config.py with the new k.
- Run `data_analysis.ipynb`
- Run `helpers/data_after_selecting_channels.ipynb`
- Create a file similar to `helpers/helpers_channels_more_300.py` for the new THRESHOLD value.
- Run the part "How to run and create an embedding" with the modified THRESHOLD value in `config.py` and
with the the new helper file
- Run the part "How to evaluate the performance of the embedding"with the modified THRESHOLD value in `config.py`and
with the the new helper file
