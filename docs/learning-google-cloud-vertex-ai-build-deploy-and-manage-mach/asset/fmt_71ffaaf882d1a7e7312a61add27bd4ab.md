
```python
tf_transform = tft.TFTransformOutput(fn_args.transform_output)

train_samples = _input_fn(_args.train_files, _args.data_accessor, tf_transform, BATCH_SIZE_TRAIN)

eval_samples = _input_fn(_args.eval_files, _args.data_accessor, tf_transform, BATCH_SIZE_EVAL)

model_classification = _make_keras_model()

model_classification.fit(
    train_samples,
    steps_per_epoch=fn_args.train_steps,
    validation_data=eval_samples,
    validation_steps=fn_args.eval_steps
)

sign = {
    "serving_default": _get_serve_tf_examples_fn(model_classification, tf_transform),
}

model_classification.save(fn_args.serving_model_dir, save_format='tf', signatures=sign)
```

1. Run the following code to copy the `trainer.py` to GCS storage:
   ```bash
   !gsutil cp trainer.py {MODULE_FOLDER}/
   ```

2. Run the following code to initiate the trainer component. `trainer_file="trainer.py"`:
   ```python
   trainer_file_path = os.path.join(MODULE_FOLDER, trainer_file)

   model_trainer = tfx.components.Trainer(
       examples=example_gen_csv.outputs["examples"],
       transform_graph=transform_data.outputs["transform_graph"],
       train_args=tfx.proto.TrainArgs(num_steps=200),
       eval_args=tfx.proto.EvalArgs(num_steps=10),
       module_file=trainer_file_path,
   )

   context_in.run(model_trainer, enable_cache=False)
   ```

The output of the trainer component is as shown in the following figure:

![](images/Figure_8.12.png)

**Figure 8.12: Output of the trainer component**

## Step 6: Creation of pipeline

Till now we have understood and executed certain components of the TFX pipeline (not all the components are needed for the pipeline construction). Let’s start constructing pipeline using `example_gen`, `statistics_gen`, `schema_gen`, `transform`, `trainer` and `pusher` components (Pusher component is used to push the trained model to a location, in this example trained model we will be pushed to the cloud storage):

* Define a function (`_create_pipeline`) consisting of all the steps/components that needs to be included in the pipeline and returns the TFX pipeline. Run the below mentioned code in a new cell to define the pipeline function:

```python
def _create_pipeline(pl_name, pipeline_root_folder, data_root,
                     module_file_transform, module_file_train, model_dir_save,
                     ) -> tfx.dsl.Pipeline:

    example_gen_csv = tfx.components.CsvExampleGen(input_base=data_root)
    gen_statistics = tfx.components.StatisticsGen(examples=example_gen_csv.outputs['examples'])
    gen_schema = tfx.components.SchemaGen(statistics=gen_statistics.outputs['statistics'])
    transform_data = tfx.components.Transform(
        examples=example_gen_csv.outputs['examples'],
        schema=gen_schema.outputs['schema'],
        module_file=os.path.join(MODULE_FOLDER, TRANSFORM_MODULE_PATH)
    )
    model_trainer = tfx.components.Trainer(
        module_file=module_file_train,
        examples=example_gen_csv.outputs['examples'],
        transform_graph=transform_data.outputs['transform_graph'],
        schema=gen_schema.outputs['schema'],
        train_args=tfx.proto.TrainArgs(num_steps=200),
        eval_args=tfx.proto.EvalArgs(num_steps=10)
    )
    pusher = tfx.components.Pusher(
        model=model_trainer.outputs['model'],
        push_destination=tfx.proto.PushDestination(
            filesystem=tfx.proto.PushDestination.Filesystem(
                base_directory=model_dir_save
            )
        )
    )
    return tfx.dsl.Pipeline(
        pipeline_name=pl_name,
        pipeline_root=pipeline_root_folder,
        components=[example_gen_csv, gen_statistics, gen_schema, transform_data, model_trainer, pusher]
    )
```

## Step 8: Defining a runner

As mentioned in the theory section, TFX is portable across environments and orchestration frameworks. TFX supports Airflow, Beam, and Kubeflow. It also provides flexibility for the developers to add their own orchestrators. Orchestrators must inherit `TfxRunner`. TFX orchestrators schedule pipeline components based on DAG dependencies using the logical pipeline object, which comprises pipeline args, components, and DAG. In our example we will be using Vertex Pipelines together with the Kubeflow V2 dag runner. In the code, we create runner using Kubeflow V2 dag and run it by passing all the pipeline parameters.

Run the following mentioned codes to define the runner:

```python
trainer_file = "trainer.py"
file_transform = os.path.join(MODULE_FOLDER, TRANSFORM_MODULE_PATH)
file_train = os.path.join(MODULE_FOLDER, trainer_file)
pl_def_file = NAME_PIPELINE + '.json'

pl_runner = tfx.orchestration.experimental.KubeflowV2DagRunner(
    config=tfx.orchestration.experimental.KubeflowV2DagRunnerConfig(),
    output_filename=pl_def_file
)

_ = pl_runner.run(
    _create_pipeline(
        pl_name=NAME_PIPELINE,
        pipeline_root_folder=ROOT_PIPELINE,
        data_root=INPUT_DATA_DIR,
        module_file_transform=file_transform,
        module_file_train=file_train,
        model_dir_save=OUTPUT_MODEL_DIR
    )
)
```

## Step 9: Pipeline execution

As the last step we need to execute the pipeline. Run the following mentioned codes in a new cell to start the pipeline execution:

```python
import google.cloud

google.cloud.aiplatform.init(project=PROJECT_ID, location="us-central1")

job = google.cloud.aiplatform.pipeline_jobs.PipelineJob(
    template_path=pl_def_file,
    display_name=NAME_PIPELINE
)

job.run(sync=False)
```

Once the pipeline starts, users will be provided the link to check the status as shown in [Figure 8.13](#ch08.xhtml#fig8-13):

![](images/Figure_8.13.png)

**Figure 8.13: Pipeline link**

1. Click on the link to check the status of the pipeline as shown in the following screenshot:

![](images/Figure_8.14.png)

**Figure 8.14: Pipeline executed successfully**

Pipeline will take a few mins to complete the training and push the trained model to the cloud storage. If the pipeline is constructed using TFX or Kubeflow, the user interface of the pipeline in GCP will remain same as shown in [Figure 8.14](#ch08.xhtml#fig8-14). Spend some time to understand each of the components and its artifacts in detail as described in the previous chapter.

## Step 10: Pipeline artifacts stored in cloud storage

Pipeline artifacts are stored in the cloud storage as shown in [Figure 8.15](#ch08.xhtml#fig8-15):

* **Module folder** contains Python files which we had pushed while creating transform and trainer components.
* **Output_model** contains trained classification model.
* **Root folder** contains artifacts of each of the component of the pipeline:

![](images/Figure_8.15.png)

**Figure 8.15: Pipeline artifacts stored in the cloud storage**

### Deletion of resources

We have utilized workbench, cloud storage to store the data and the artifacts of the pipeline. For deletion of resources, ensure to delete the workbench, clear the data stored in the cloud storage.

### Conclusion

We learnt about the TFX, a few of its components and constructed pipeline using some of the standard components. Also, we understood how to use Kubeflow for the orchestration of TFX pipeline on Vertex AI.

In the next chapter, we will start understanding and working on feature store of the Vertex AI.

### Questions

1. Which artifacts of the transform component is used in the training component of the pipeline?
2. What are the different orchestration options TFX supports?
3. Try using evaluator component between trainer and pusher component and re-construct the pipeline. (Use evaluator component to evaluate the model performance and push it only if the performance is good).

### Join our book’s Discord space

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

**[https://discord.bpbonline.com](https://discord.bpbonline.com)**

![](images/fm1.png)

# CHAPTER 9: Vertex AI Feature Store
