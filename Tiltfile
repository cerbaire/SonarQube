set_team('111460f6-21cd-4430-be50-8898c8938875')
allow_k8s_contexts(['docker-desktop'])
load('ext://restart_process', 'docker_build_with_restart')
load('ext://namespace', 'namespace_yaml')
k8s_yaml(namespace_yaml('sonar'))
yaml = helm(
    './chart',                          # Path to the chart dir
    name='sonar',                   # The release name, equivalent to helm --name
    namespace='sonar',                  # The namespace to install in, equivalent to helm --namespace
    values=['./chart/values-dev.yaml'], # The values file to substitute into the chart.
    )
# Deploy: tell Tilt what YAML to deploy
k8s_yaml(yaml)

k8s_resource('sonarqube', port_forwards=9000,
  resource_deps=[]
)
