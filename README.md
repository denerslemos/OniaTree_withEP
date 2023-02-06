# OniaTree with EP in pPb at 8.16 TeV

Intructions to run onia tree framework in pPb including the Event plane information after flattening and also saves PU filters as integers (0 is bad event and 1 is good event) that can be applied later in analysis. 

```
# Adapted from https://twiki.cern.ch/twiki/bin/viewauth/CMS/HiDileptonWorkingAreaSetting#CMSSW_80X
cmsrel CMSSW_8_0_26_patch2
cd CMSSW_8_0_26_patch2/src/
cmsenv

# Bring a working branch from remote repository
git cms-merge-topic CMS-HIN-dilepton:Onia_PA_8_0_X

git cms-addpkg HiSkim/HiOnia2MuMu
git cms-addpkg HiAnalysis/HiOnia
git cms-addpkg RecoHI/Configuration

# Adding EP information and flattening
cp -r /afs/cern.ch/work/d/ddesouza/public/ForOniaTree_pPb/CondFormats $CMSSW_BASE/src/
cp -r /afs/cern.ch/work/d/ddesouza/public/ForOniaTree_pPb/HiEvtPlaneAlgos $CMSSW_BASE/src/RecoHI/
cp -r /afs/cern.ch/work/d/ddesouza/public/ForOniaTree_pPb/HiEvtPlaneCalib $CMSSW_BASE/src/HeavyIonsAnalysis/
cp -r /afs/cern.ch/work/d/ddesouza/public/ForOniaTree_pPb/QWNtrkOfflineProducer $CMSSW_BASE/src/HeavyIonsAnalysis/
cp -r /afs/cern.ch/work/d/ddesouza/public/ForOniaTree_pPb/VNAnalysis $CMSSW_BASE/src/HeavyIonsAnalysis/

# Adding PU filters (== 0 is false -> bad event; == 1 is true --> good event)
cp -r /afs/cern.ch/work/d/ddesouza/public/ForOniaTree_pPb/HiOniaAnalyzer.cc $CMSSW_BASE/src/HiAnalysis/HiOnia/plugins/

# Adding new cfg and crab ( you can work in the workstation folder :) )
cp -r /afs/cern.ch/work/d/ddesouza/public/ForOniaTree_pPb/workstation $CMSSW_BASE/src/HiAnalysis/HiOnia/test/

scram b -j 12

cd $CMSSW_BASE/src/HiAnalysis/HiOnia/test/workstation
```
