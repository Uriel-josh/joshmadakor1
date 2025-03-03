import React from 'react';
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card';
import { LineChart, Line, BarChart, Bar, PieChart, Pie, AreaChart, Area, XAxis, YAxis, CartesianGrid, Tooltip, Legend, ResponsiveContainer, Cell } from 'recharts';
import { Tabs, TabsContent, TabsList, TabsTrigger } from '@/components/ui/tabs';
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from '@/components/ui/select';

const RegionalEconomicImpactAnalysis = () => {
  // Sample data - in a real implementation, this would come from SQL database
  const gdpData = [
    { month: 'Jan', region1: 3.2, region2: 2.8, region3: 3.5 },
    { month: 'Feb', region1: 3.3, region2: 2.7, region3: 3.6 },
    { month: 'Mar', region1: 3.4, region2: 2.9, region3: 3.4 },
    { month: 'Apr', region1: 3.6, region2: 3.0, region3: 3.5 },
    { month: 'May', region1: 3.8, region2: 3.1, region3: 3.7 },
    { month: 'Jun', region1: 3.9, region2: 3.2, region3: 3.8 },
    { month: 'Jul', region1: 4.0, region2: 3.3, region3: 3.9 },
  ];

  const unemploymentData = [
    { month: 'Jan', region1: 5.8, region2: 4.9, region3: 6.2 },
    { month: 'Feb', region1: 5.7, region2: 4.8, region3: 6.1 },
    { month: 'Mar', region1: 5.6, region2: 4.7, region3: 6.0 },
    { month: 'Apr', region1: 5.5, region2: 4.6, region3: 5.9 },
    { month: 'May', region1: 5.4, region2: 4.5, region3: 5.8 },
    { month: 'Jun', region1: 5.3, region2: 4.4, region3: 5.7 },
    { month: 'Jul', region1: 5.2, region2: 4.3, region3: 5.6 },
  ];

  const inflationData = [
    { month: 'Jan', region1: 2.1, region2: 1.8, region3: 2.3 },
    { month: 'Feb', region1: 2.2, region2: 1.9, region3: 2.4 },
    { month: 'Mar', region1: 2.3, region2: 2.0, region3: 2.5 },
    { month: 'Apr', region1: 2.4, region2: 2.1, region3: 2.6 },
    { month: 'May', region1: 2.5, region2: 2.2, region3: 2.7 },
    { month: 'Jun', region1: 2.6, region2: 2.3, region3: 2.8 },
    { month: 'Jul', region1: 2.7, region2: 2.4, region3: 2.9 },
  ];

  const industryContribution = [
    { name: 'Manufacturing', value: 28 },
    { name: 'Services', value: 42 },
    { name: 'Agriculture', value: 15 },
    { name: 'Technology', value: 15 },
  ];

  const regionalComparison = [
    { name: 'Region 1', gdp: 4.0, unemployment: 5.2, inflation: 2.7 },
    { name: 'Region 2', gdp: 3.3, unemployment: 4.3, inflation: 2.4 },
    { name: 'Region 3', gdp: 3.9, unemployment: 5.6, inflation: 2.9 },
    { name: 'National Avg', gdp: 3.7, unemployment: 5.0, inflation: 2.5 },
  ];

  const COLORS = ['#0088FE', '#00C49F', '#FFBB28', '#FF8042'];

  return (
    <div className="w-full p-4 bg-gray-50">
      <div className="mb-8">
        <h1 className="text-3xl font-bold text-gray-900">Regional Economic Impact Analysis</h1>
        <p className="text-gray-600 mt-2">Interactive dashboard analyzing economic indicators across regions</p>
        
        <div className="flex items-center mt-4 space-x-4">
          <Select defaultValue="q2-2023">
            <SelectTrigger className="w-32">
              <SelectValue placeholder="Time Period" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value="q1-2023">Q1 2023</SelectItem>
              <SelectItem value="q2-2023">Q2 2023</SelectItem>
              <SelectItem value="q3-2023">Q3 2023</SelectItem>
              <SelectItem value="q4-2023">Q4 2023</SelectItem>
            </SelectContent>
          </Select>
          
          <Select defaultValue="all">
            <SelectTrigger className="w-32">
              <SelectValue placeholder="Region" />
            </SelectTrigger>
            <SelectContent>
              <SelectItem value="all">All Regions</SelectItem>
              <SelectItem value="region1">Region 1</SelectItem>
              <SelectItem value="region2">Region 2</SelectItem>
              <SelectItem value="region3">Region 3</SelectItem>
            </SelectContent>
          </Select>
        </div>
      </div>

      <div className="grid grid-cols-1 md:grid-cols-3 gap-6 mb-6">
        <Card>
          <CardHeader className="pb-2">
            <CardTitle className="text-lg">GDP Growth Rate</CardTitle>
          </CardHeader>
          <CardContent>
            <div className="text-3xl font-bold text-blue-600">3.7%</div>
            <div className="text-sm text-green-500 mt-1">↑ 0.3% from previous quarter</div>
          </CardContent>
        </Card>
        
        <Card>
          <CardHeader className="pb-2">
            <CardTitle className="text-lg">Unemployment Rate</CardTitle>
          </CardHeader>
          <CardContent>
            <div className="text-3xl font-bold text-blue-600">5.4%</div>
            <div className="text-sm text-green-500 mt-1">↓ 0.2% from previous quarter</div>
          </CardContent>
        </Card>
        
        <Card>
          <CardHeader className="pb-2">
            <CardTitle className="text-lg">Inflation Rate</CardTitle>
          </CardHeader>
          <CardContent>
            <div className="text-3xl font-bold text-blue-600">2.5%</div>
            <div className="text-sm text-red-500 mt-1">↑ 0.1% from previous quarter</div>
          </CardContent>
        </Card>
      </div>

      <Tabs defaultValue="overview" className="mb-6">
        <TabsList className="mb-4">
          <TabsTrigger value="overview">Overview</TabsTrigger>
          <TabsTrigger value="gdp">GDP Analysis</TabsTrigger>
          <TabsTrigger value="unemployment">Unemployment</TabsTrigger>
          <TabsTrigger value="inflation">Inflation</TabsTrigger>
        </TabsList>
        
        <TabsContent value="overview">
          <div className="grid grid-cols-1 lg:grid-cols-2 gap-6">
            <Card>
              <CardHeader>
                <CardTitle>Regional Comparison</CardTitle>
              </CardHeader>
              <CardContent className="h-72">
                <ResponsiveContainer width="100%" height="100%">
                  <BarChart data={regionalComparison}>
                    <CartesianGrid strokeDasharray="3 3" />
                    <XAxis dataKey="name" />
                    <YAxis />
                    <Tooltip />
                    <Legend />
                    <Bar dataKey="gdp" name="GDP Growth %" fill="#0088FE" />
                    <Bar dataKey="unemployment" name="Unemployment %" fill="#FF8042" />
                    <Bar dataKey="inflation" name="Inflation %" fill="#FFBB28" />
                  </BarChart>
                </ResponsiveContainer>
              </CardContent>
            </Card>
            
            <Card>
              <CardHeader>
                <CardTitle>Industry Contribution to GDP</CardTitle>
              </CardHeader>
              <CardContent className="h-72">
                <ResponsiveContainer width="100%" height="100%">
                  <PieChart>
                    <Pie
                      data={industryContribution}
                      cx="50%"
                      cy="50%"
                      labelLine={true}
                      label={({ name, percent }) => `${name}: ${(percent * 100).toFixed(0)}%`}
                      outerRadius={80}
                      fill="#8884d8"
                      dataKey="value"
                    >
                      {industryContribution.map((entry, index) => (
                        <Cell key={`cell-${index}`} fill={COLORS[index % COLORS.length]} />
                      ))}
                    </Pie>
                    <Tooltip />
                  </PieChart>
                </ResponsiveContainer>
              </CardContent>
            </Card>
          </div>
        </TabsContent>
        
        <TabsContent value="gdp">
          <Card>
            <CardHeader>
              <CardTitle>GDP Growth Trend by Region</CardTitle>
            </CardHeader>
            <CardContent className="h-96">
              <ResponsiveContainer width="100%" height="100%">
                <LineChart data={gdpData}>
                  <CartesianGrid strokeDasharray="3 3" />
                  <XAxis dataKey="month" />
                  <YAxis label={{ value: 'GDP Growth (%)', angle: -90, position: 'insideLeft' }} />
                  <Tooltip />
                  <Legend />
                  <Line type="monotone" dataKey="region1" name="Region 1" stroke="#0088FE" activeDot={{ r: 8 }} />
                  <Line type="monotone" dataKey="region2" name="Region 2" stroke="#00C49F" />
                  <Line type="monotone" dataKey="region3" name="Region 3" stroke="#FFBB28" />
                </LineChart>
              </ResponsiveContainer>
            </CardContent>
          </Card>
        </TabsContent>
        
        <TabsContent value="unemployment">
          <Card>
            <CardHeader>
              <CardTitle>Unemployment Rate Trend by Region</CardTitle>
            </CardHeader>
            <CardContent className="h-96">
              <ResponsiveContainer width="100%" height="100%">
                <AreaChart data={unemploymentData}>
                  <CartesianGrid strokeDasharray="3 3" />
                  <XAxis dataKey="month" />
                  <YAxis label={{ value: 'Unemployment Rate (%)', angle: -90, position: 'insideLeft' }} />
                  <Tooltip />
                  <Legend />
                  <Area type="monotone" dataKey="region1" name="Region 1" stroke="#0088FE" fill="#0088FE" fillOpacity={0.3} />
                  <Area type="monotone" dataKey="region2" name="Region 2" stroke="#00C49F" fill="#00C49F" fillOpacity={0.3} />
                  <Area type="monotone" dataKey="region3" name="Region 3" stroke="#FFBB28" fill="#FFBB28" fillOpacity={0.3} />
                </AreaChart>
              </ResponsiveContainer>
            </CardContent>
          </Card>
        </TabsContent>
        
        <TabsContent value="inflation">
          <Card>
            <CardHeader>
              <CardTitle>Inflation Rate Trend by Region</CardTitle>
            </CardHeader>
            <CardContent className="h-96">
              <ResponsiveContainer width="100%" height="100%">
                <LineChart data={inflationData}>
                  <CartesianGrid strokeDasharray="3 3" />
                  <XAxis dataKey="month" />
                  <YAxis label={{ value: 'Inflation Rate (%)', angle: -90, position: 'insideLeft' }} />
                  <Tooltip />
                  <Legend />
                  <Line type="monotone" dataKey="region1" name="Region 1" stroke="#0088FE" />
                  <Line type="monotone" dataKey="region2" name="Region 2" stroke="#00C49F" />
                  <Line type="monotone" dataKey="region3" name="Region 3" stroke="#FFBB28" />
                </LineChart>
              </ResponsiveContainer>
            </CardContent>
          </Card>
        </TabsContent>
      </Tabs>

      <Card>
        <CardHeader>
          <CardTitle>Key Insights</CardTitle>
        </CardHeader>
        <CardContent>
          <ul className="space-y-2">
            <li className="flex items-start">
              <div className="bg-green-100 text-green-800 p-1 rounded mr-2 mt-1">↑</div>
              <span>Region 1 shows consistent GDP growth, outperforming other regions with a 4.0% rate in July.</span>
            </li>
            <li className="flex items-start">
              <div className="bg-green-100 text-green-800 p-1 rounded mr-2 mt-1">↓</div>
              <span>Unemployment is steadily decreasing across all regions, with Region 2 achieving the lowest rate at 4.3%.</span>
            </li>
            <li className="flex items-start">
              <div className="bg-yellow-100 text-yellow-800 p-1 rounded mr-2 mt-1">⚠</div>
              <span>Inflation shows an upward trend across all regions, potentially indicating economic pressure.</span>
            </li>
            <li className="flex items-start">
              <div className="bg-blue-100 text-blue-800 p-1 rounded mr-2 mt-1">i</div>
              <span>The services sector is the largest contributor to regional GDP at 42%, followed by manufacturing at 28%.</span>
            </li>
          </ul>
        </CardContent>
      </Card>
    </div>
  );
};

export default RegionalEconomicImpactAnalysis;
