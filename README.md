# branch-predictor Using Python

Tool for visualizing and comparing different dynamic branch prediction methods for a pipelined processor.

Currently only shows branch direction predictions (taken or not taken), Since these can generally be done efficiently for direct branches with a branch target buffer (BTB) and return address stack (RAS) for function returns.  

Note that this tool is simply to be used for visualizing and better understanding branch prediction accuracy of different branch prediction methods under different branch patterns, not for rigorous testing for comparison between the methods.  

## Branch prediction methods includes
- Compare between simple n-bit saturating counters or simulate custom branch predictor with the following architecture and choices:
![alt text](assets/general_architecture.png)
- BHT different entry types
    - n-bit saturating counters
    - n-bit agree predictor 
        - The "Bias Bit Table" displayed would likely be part of the BTB or I-cache.
![alt text](assets/bht_entry_choices.png)
- Different Indexing methods for BHT
    - PC
    - GHR
    - GHR XOR PC (GShare)
    - PHT entry XOR PC (PShare)
    - PC index PHT, PHT entry index BHT (Local History)
![alt text](assets/indexing_choices.png)
- Input: list of (PC of branch instruction, T or NT)

## Usage and Dependencies
- Tkinter and pillow libraries are necessary.
- and launch/run `main.py` with Python.

- Below is an example simulation of branch prediction with 8-entry branch history table.
![alt text](assets/local_history_example.png)  
- Example text files are provided in `examples/` for simulating branch instructions from a file upload. PC values can be of any length. See [`examples/README.md`](examples/README.md) for more details.

## References
- McFarling, "[Combining Branch Predictors](https://www.hpl.hp.com/techreports/Compaq-DEC/WRL-TN-36.pdf?source=aw&subacctid=78888&subacctname=Skimlinks&adcampaigngroup=91539&awc=7168_1634183649_7110ed148465d8d1f132fb09063d57ff&jumpid=af_gen_nc_ns&utm_medium=af&utm_source=aw&utm_campaign=Skimlinks)," DEC WRL Technical
Report, 1993.
- Sprangle et al., "[The agree predictor: a mechanism for reducing negative branch history interference](https://doi.org/10.1145/384286.264210)," ISCA 1997
- Yeh and Patt, "[Two-Level Adaptive Training Branch Prediction](https://www.inf.pucrs.br/~calazans/graduate/SDAC/saltos.pdf)," MICRO 1991.
- ECE 3058, [GT HPCA](https://www.youtube.com/watch?v=tawb_aeYQ2g&list=PLAwxTw4SYaPmqpjgrmf4-DGlaeV0om4iP), and [CMU 18-740](https://www.youtube.com/watch?v=M0y_Nvb9rGA&list=PL5PHm2jkkXmgVhh8CHAu9N76TShJqfYDt) lectures.
- cwang360 / [branch-prediction-visualization](https://github.com/cwang360/branch-prediction-visualization)
