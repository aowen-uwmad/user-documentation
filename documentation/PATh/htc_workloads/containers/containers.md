---
path:
    path: htc_workloads/containers/containers.md
---

Software Containers
===================

Docker and Apptainer/Singularity are container systems that allow users full
control over their software environment. You can create your own
container image or choose from a set of pre-defined images, and specify
that your submitted jobs run within one of these.

For jobs on the PATh Facility, it does not matter whether you provide a Docker or
Apptainer/Singularity image. Either is compatible with our system and can be
used with minimal to no modification. Determining factors on when to
use Apptainer/Singularity images over Docker images include if an image already
exists, external to PATh distribution preferences, and if you have
experience building images in one for format and not the other.

Because the PATh Facility is a distributed infrastructure and workloads consists
of a large number jobs (and there container executions), it is
important to consider how the container image is transferred to
the execution nodes. The instructions below contain best practices
when it comes to access both Apptainer/Singularity and Docker images.

When using a container for your jobs, the container image is
automatically started up when HTCondor matches your job to a slot. The
executable provided in the submit script will be run within the context
of the container image, having access to software and libraries that
were installed to the image, as if they were already on the server where
the job is running. Job executables need not (and should not) run any
commands to start the container. Nor should the container image
contain any entrypoint/cmd - the job is the command to be run in the
container.

## PATh-Provided Images

The Facilition Team maintains a set of images that are already in a shared 
Apptainer/Singularity repository. *[A list of available containers can be found on this page][container-list].*

If the software you need isn't already supported in a listed container,
you can use your own container or any container image in Docker Hub
(see sections further below). Once the container you need is in the
Apptainer/Singularity repository, your can submit jobs that run within a
particular container by listing the container image in the submit file.

    +SingularityImage = "osdf:///ospool/uc-shared/public/OSG-Staff/images/repo/x86_64/htc__rocky__9.sif"

    <other usual submit file lines>
    queue

## Custom Apptainer Images

If you already have software in the form of a `.sif` Apptainer/Singuilarity file,
you can stage the .sif file with your job. For small workloads, sending
the file with the job is ok:

    transfer_input_files = my-custom-image-v1.sif
    +SingularityImage = "my-custom-image-v1.sif"

For larger workloads, the image will be resused for
each job, and thus the preferred transfer method is an OSDF tool.
Store the .sif file under `/path-facility/data/$USER/`, and then use the OSDF
url directly in the `+SingularityImage` attribute. Note that you can not
use shell variable expansion in the submit file - be sure to replace the
username with your actual PATh Facility username. Example:

    +SingularityImage = "osdf:///path-facility/data/USERNAME/my-custom-image-v1.sif"

    <other usual submit file lines>
    queue

**Be aware that the OSDF aggressively caches the image based on file naming.
If you need to do quick changes, please use versioning of the .sif file
so that the caches see a "new" name.** In this example, replacing
`my-custom-image-v1.sif` with new content will probably mean that some
nodes get the old version and some nodes the new version. Prevent this
by creating a new file named with v2.

More information on how to create Apptainer/Singularity images can be found
in the [Apptainer Images Guide][singularity-guide].

If you already have a Docker image, or want to build one, see 
our [Docker Images Guide][docker-guide]. 

[container-list]: available-containers-list
[docker-guide]: containers-docker
[singularity-guide]: containers-singularity
