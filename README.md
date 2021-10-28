# Import Template

Deployments, pipelines and environment variables can be imported and exported in UbiOps. This is useful when you want
to share your deployments and pipelines, want to copy them to another project, want to make a back-up, or when you
prefer to create objects using yaml files. The structure of such import file is shown in this repository. Zip the
directory `import` of this repository and upload it to UbiOps to import 2 simple deployments and 1 pipeline.

## Import file structure

An import file should have the structure as described below. Any export you make will automatically follow this
structure so that it is easy to import later.

- **import.zip**

    - **import&#47;**

        *The name of the root directory doesn't matter*

        - **info.yaml**

            *This file contains at least `format_spec`, which is the version of the import format, e.g., 'v1.0'*

        - **deployments&#47;** 	(optional)

            *This directory contains all deployments that you want to import. In this case, just `deployment-1`.*

            - **deployment_deployment-1&#47;**

                *This is an example of a deployment to import. The name of the directory doesn't matter, but it usually
                contains the deployment name.*

                - **deployment_deployment-1.yaml**

                    *Required settings file of the deployment. This file may contain all deployment parameters, and
                    should at least provide the required fields `deployment_name`, `input_type` and `output_type`. You
                    may want to include deployment environment variables using `deployment_environment_variables`.*

                - **versions&#47;**  (optional)

                    *This directory contains all versions of `deployment-1` that you want to import. In this case, just
                    `v1`.*

                    - **deployment_deployment-1_version_v1.yaml**

                        *Required settings file of the deployment version. This file may contain all version parameters,
                        and should at least provide the required field `version_name`. You may want to include version
                        environment variables using `version_environment_variables`.*

                    - **deployment_deployment-1_version_v1.zip**

                        *Optional deployment package ZIP file of the deployment version. The file must have the same
                        name as the version yaml file it belongs to, only with a .zip extension instead.*

        - **pipelines&#47;**  (optional)

            *This directory contains all pipelines that you want to import. In this case, just `pipeline-1`.*

            - **pipeline_pipeline-1&#47;**

                *This is an example of a pipeline to import. The name of the directory doesn't matter, but usually
                contains the pipeline name.*

                - **pipeline_pipeline-1.yaml**

                    *Required settings file of the pipeline. This file may contain all pipeline parameters, and should
                    at least provide the required fields `pipeline_name`, `input_type` and `output_type`.*

                - **versions&#47;**  (optional)

                    *This directory contains all versions of `pipeline-1` that you want to import. In this case, just
                    `v1`.*

                    - **pipeline_pipeline-1_version_v1.yaml**

                        *Required settings file of the pipeline version. This file may contain all version parameters,
                        and should at least provide the required field `version_name`.*
