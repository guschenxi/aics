### Agents in virtual environment

Framework: Habitat Lab (in conjunction with Habitat Sim), tag v.0.2.1, [link](https://github.com/facebookresearch/habitat-lab/tree/v0.2.1)

Tasks: Embodied Question Answering, [link](https://github.com/facebookresearch/habitat-lab/tree/v0.2.1/habitat_baselines/il)

Data: from the original repository or from ``/srv/data/aics/habitat-lab/data``
P.S. Train and evaluation datasets for EQA are created incrementally; once you ran the script, they are cached on the servers.


#### Running Habitat Lab on MLT-GPU

Run

``$ module load habitat``

This will place you in the global Habitat environment.

You can test whether Habitat works for you by running

``$ cd /usr/local/habitat/habitat-lab``

``$ python example/example.py``

This should print the number of steps for an episode.

You might want to set ``MAGNUM_GPU_VALIDATION=ON`` if the example script does not work.


#### Running EQA on MLT-GPU

Train or evaluate pre-trained CNN model:

``LD_LIBRARY_PATH=/usr/local/miniconda3/lib/
python -u habitat_baselines/run.py --exp-config habitat_baselines/config/eqa/il_eqa_cnn_pretrain.yaml --run-type {TYPE}``

where TYPE is either train or eval.

Don't forget to fix paths in ``il_eqa_cnn_pretrain.yaml`` file.


Train or evaluate pre-trained VQA model:

``LD_LIBRARY_PATH=/usr/local/miniconda3/lib/
python -u habitat_baselines/run.py --exp-config habitat_baselines/config/eqa/il_vqa.yaml --run-type {TYPE}``

where TYPE is either train or eval.

Don't forget to fix paths in ``il_vqa.yaml`` file.

