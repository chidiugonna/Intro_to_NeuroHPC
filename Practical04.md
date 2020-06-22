# Practical 04 Upload and Download data



## Objectives 04

- Explore upload of files and folders to the HPC and download of files and folders from HPC
  - HPC transferring files https://public.confluence.arizona.edu/display/UAHPC/Transferring+Files
  - Benchmarks from HPC here https://github.com/SaraMWillis/Cloud_Storage_Benchmarking
  - Storage information here https://public.confluence.arizona.edu/display/UAHPC/Storage
- Chosen approach will depend on requirements:
  - Speed of transfer
  - Robustness to error
  - Security of transfer
  - Ease of use
  - Reusability/Flexibiliy of transfer settings
  - Sharability




### Exercise 04.A: Download/Upload files from/to local computer to/from HPC

- Using **Open on Demand** (unfortunately uploads restricted to < 64 MB, Downloads are unrestricted). This can be used for quickly transferring small files or folders to the HPC.
  - Navigate to Open on Demand and click on "Files" 
  - Simply drag and drop any appropriately sized folder and/or files onto a  remote folder that you have access to.
- Download `bids001928.zip` from https://osf.io/gqk6n/ to your local computer
- Using the **command line** we can upload the `bids001928.zip` file to the HPC:
  - use `scp /localpath/to/file netid@filexfer.hpc.arizona.edu:/remotepath/to/file` to transfer individual files. swap the source and destination to download files from HPC to local computer.
  - use the `-r` parameter as in ``scp -r /localpath/to/folder netid@filexfer.hpc.arizona.edu:/remotepath/to/folder` to copy folder and contents
  - instead of `scp` you can also use `rsync` if available for more sophisticated file transfers that support restart after interruption with `rsync -P` and which will generally operate much faster than scp especially for larger transfer jobs.
  - Another option is to use `sftp` to use ftp from local machine to the HPC as in `sftp netid@sftp.hpc.arizona.edu` then files can be retrieved using `get` or `reget` and transferred using `put` or `reput` 
- Using a **Gui client** like **CyberDuck** or on **windows WinSCP** - these are fairly straightforward to use and allow easy transfer between HPC and local computer and in the case of cyberduck between GoogleDrive and the local computer.
- Using **Globus** - the **GUI Client** can be downloaded and installed on a local computer. The **Globus CLI** can be installed as a python executable using `pip install --user globus-cli` or using anaconda using `conda install -c conda-forge globus-cli` on the local computer or on the HPC.



### Exercise : Download files from OSF using osfclient

We can use the osfclient module to directly fetch files from the osf public site https://osf.io/gqk6n/  that holds the data

```
module load python/3.5/3.5.5
pip install --user osfclient

mkdir -p nifti
cd nifti

osf -p gqk6n fetch /Data/nifti.zip nifti.zip
unzip nifti.zip
rm nifti.zip

rm -rf logs
rm -rf tmp_dcm2bids
```



### Exercise : Download files from HPC to Google Drive

- Files can be transferred between **Google Drive** and the **HPC** using the **Cyberduck CLI**

- Also possible to do this using Globus