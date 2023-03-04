Build container:

    docker build \
        --tag unam-uime-jupyter:scipy-notebook \
        --build-arg genomx=`getent group genomx | cut -d: -f3` \
        ./jupyter-notebook/

Run container:
    docker run --detach \
        -p 8888:8888 \
        --name jupy-scipynotebook-6_5_2\
        --volume "/Data/A/dockerapps/jupy-scn:/Data:ro" \
        --volume "/home/:/home/" \
        unam-uime-jupyter:scipy-notebook

Run container ya bien:
    docker run --detach \
        -p 8888:8888 \
        --name jupy-scipynotebook-6_5_2\
        --env "VIRTUAL_HOST=jupyter.genomx.be" \
        --env "LETSENCRYPT_HOST=jupyter.genomx.be" \
        --volume "/Data/A/dockerapps/bio-r:/Data:ro" \
        --volume "/home/:/home/" \
        unam-uime-bior:bioconductor 