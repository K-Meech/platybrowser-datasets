# Segmentation Methods

Different methods were used to segment the structures of interest in the EM-Volume:
- cells: Cell membranes were segmented with a [3d U-Net](https://link.springer.com/chapter/10.1007/978-3-319-46723-8_49) trained with [long-range affinity loss](https://arxiv.org/abs/1706.00120). Based on these predictions, instance segmentation was performed via [Lifted Multicut workflow](https://www.frontiersin.org/articles/10.3389/fcomp.2019.00006/full), including priors from the nucleus segmentation.
- chromatin: [Ilastik](https://www.nature.com/articles/s41592-019-0582-9) pixel classification was used, restricted to the segmented nuclei.
- cilia: Cilia boundaries were segmented with a [3d U-Net](https://link.springer.com/chapter/10.1007/978-3-319-46723-8_49) trained with [long-range affinity loss](https://arxiv.org/abs/1706.00120). Based on these predictions, instance segmentation was performed via [Mutex Watershed](http://openaccess.thecvf.com/content_ECCV_2018/html/Steffen_Wolf_The_Mutex_Watershed_ECCV_2018_paper.html) and [Block-wise Multicut](http://openaccess.thecvf.com/content_ICCV_2017_workshops/w1/html/Pape_Solving_Large_Multicut_ICCV_2017_paper.html).
- cuticle: Cuticle boundaries were segmented with a [3d U-Net](https://link.springer.com/chapter/10.1007/978-3-319-46723-8_49) trained with [long-range affinity loss](https://arxiv.org/abs/1706.00120). Based on these predictions, instance segmentation was performed via [Mutex Watershed](http://openaccess.thecvf.com/content_ECCV_2018/html/Steffen_Wolf_The_Mutex_Watershed_ECCV_2018_paper.html) and [Block-wise Multicut](http://openaccess.thecvf.com/content_ICCV_2017_workshops/w1/html/Pape_Solving_Large_Multicut_ICCV_2017_paper.html).
- ganglia: The ganglia were segmented by manually selecting the ids of segmented cells.
- nuclei: Nuclear membranes were segmented with a [3d U-Net](https://link.springer.com/chapter/10.1007/978-3-319-46723-8_49) trained with [long-range affinity loss](https://arxiv.org/abs/1706.00120). Based on these predictions, instance segmentation was performed via [Mutex Watershed](http://openaccess.thecvf.com/content_ECCV_2018/html/Steffen_Wolf_The_Mutex_Watershed_ECCV_2018_paper.html) and [Block-wise Multicut](http://openaccess.thecvf.com/content_ICCV_2017_workshops/w1/html/Pape_Solving_Large_Multicut_ICCV_2017_paper.html).
- tissue: Tissue and regions were segmented using the  [Ilastik carving workflow](https://www.nature.com/articles/s41592-019-0582-9)

If you use any of the segmentation functionality provided, please cite the [main publication](https://www.biorxiv.org/content/10.1101/2020.02.26.961037v1) AND the appropriate methods. 
For most of these methods, the scalable implementations in [cluster tools](https://github.com/constantinpape/cluster_tools) were used.

Training data and weights for the 3d U-Nets are available on zenodo:
- cells: [Training Data](https://zenodo.org/record/3675220/files/membrane.zip?download=1), [Weights](https://zenodo.org/record/3675288/files/cilia.nn?download=1)
- cilia: [Training Data](https://zenodo.org/record/3675220/files/cilia.zip?download=1), [Weights](https://zenodo.org/record/3675288/files/cuticle.nn?download=1)
- cuticle: [Training Data](https://zenodo.org/record/3675220/files/cuticle.zip?download=1), [Weights](https://zenodo.org/record/3675288/files/membranes.nn?download=1)
- nuclei: [Training Data](https://zenodo.org/record/3675220/files/nuclei.zip?download=1), [Weights](https://zenodo.org/record/3675288/files/nuclei.nn?download=1)

The models are also available on [bioimage.io](https://bioimage.io/) in order to run them in [Deep Ilastik](https://www.ilastik.org/) (still in beta).

The ilastik project and training data for the chromatin segmentation are also [available on zenodo](https://doi.org/10.5281/zenodo.3676534), as well as the [ilastik projects for carving out tissue/body parts and the animal outline](https://doi.org/10.5281/zenodo.3678793).

In addition, we provide scripts to validate cell and nucleus segmentations. The validation data, which consists of annotations for nuclei and cell soma from 8 domain experts, [is available on zenodo](https://doi.org/10.5281/zenodo.3690727).
